# Notes from running CPSC 515 M2 (2020W1 edition) in Windows 10

Find instructions for this milestone at the [class Github repository](https://github.com/ian-mitchell/CPSC-515-2020W1/blob/master/Milestone%202%20-%20Basic%20Robot%20Simulation%20with%20Gazebo/M2.md).

* Gazebo is installed (in the form of the `gazebo-9` package) as part of `ros-melodic-desktop_full` metapackage through chocolatey.
  * Gazebo should find them automatically, but FYI the `.launch` and `.world` files are in subdirectories of
    ```
    c:/opt/ros/melodic/x64/share/
    ```
  * I have not figured out how to run `gzserver` and `gzclient` separately, but 
    ```
    $ roslaunch gazebo_ros empty_world.launch paused:=true use_sim_time:=false gui:=true throttled:=false recording:=false debug:=true verbose:=true gui_required:=true
    ``` 
    as suggested in the [Using roslaunch to start Gazebo...](http://gazebosim.org/tutorials?tut=ros_roslaunch&cat=connect_ros) tutorial worked fine.
  * The `gazebo` command (combining `gzserver` and `gzclient`) is undefined, so use `roslaunch` as above.
  * The default for `GAZEBO_MODEL_PATH` appears to be `C:\Users\<your-windows-user-name>\.gazebo\models\`; however, even though `C:\Users\<your-windows-user-name>\.gazebo` is created automatically it looks like the `models\` subdirectory is not.  The result is that attempts to add new models to the world (for example, from [http://models.gazebosim.org]) fails.  The fix appears to be simple: Create the `models\` subdirectory manually.

* `tf2` tutorial.
  * There is no `apt-get` in Windows, and there are no packages at `https://aka.ms/ros/public` corresponding to `ros-melodic-turtle-tf2`, `ros-melodic-tf2-tools` or `ros-melodic-tf`.  However, there are `tf` related packages already installed as part of `ros-melodic-desktop_full`, and all of the tutorial appears to work *except* that there is no `view_frames.py` (from section 4.1), or indeed any `tf2_tools` in the ROS directory structure.  Fortunately, that particular feature appears to be superfluous.
  * To run `rviz` manually I found that I needed to provide the full path to the `turtle_tf2` `.rviz` file.  So instead of
    ```
    $ rosrun rviz rviz -d `rospack find turtle_tf2`/rviz/turtle_rviz.rviz
    ```
    I had to run
    ```
    $ rospack find turtle_tf2
    ```
    copy the result and add it to the command; for example,
    ```
    rosrun rviz rviz -d c:\opt\ros\melodic\x64\share\turtle_tf2\rviz\turtle_rviz.rviz
    ```

* URDF tutorials.
  * The `urdf_tutorial` package is installed in `<ros directory>/share`.
  * The remaining packages for these tutorials appear to have been included in `ros-melodic-desktop_full`.

## Attempt to install Gazebo independently

Based on [Gazebo](http://gazebosim.org/)'s [Install on Windows](http://gazebosim.org/tutorials?tut=install_on_windows&cat=install) instructions.

Two stages of this attempt failed, one optional (see below) and the other critical (the final build of `gzclient`).  At this time I do not recommend following these instructions.

* Used `cygwin` for steps 2, 3, and 6 and the VS command prompt (set up during ROS installation) for steps 8-15.  Not sure if step 7 is necessary because we are running inside the VS command prompt.  I did not install `cmake` (step 4) or `ruby` (step 5), since they were already installed in both `cygwin` and the VS command prompt.
  * Definitely worth writing a script to use `wget` to download and `unzip` the dependencies listed in step 2 & 3.  Probably worth looking to see whether those dependencies can be downloaded and managed through `vcpkg` instead of doing it manually.  Ended up using `7-zip` to unpack the zip files because `cygwin`'s `unzip` command did not handle wildcards well.
  * Note that unzipping all of these archives dumps files into common `bin\`, `include\`, `lib\`, and `share\` subdirectories, so you will not see new subdirectories for every package from step 2 after unzipping in step 3.
  * In step 6, observe that the `-b` flag at the end of the `git clone` commands is ensuring that you are checking out the version of the packages compatible with Gazebo 9.

* Significant problems were encountered during installation of the Ignition packages in steps 8-15.
  * The `configure` script for these steps starts with lines of the form
    ```
    call %win_lib% :download_unzip_install dlfcn-win32-vc15-x64-dll-MD.zip
    ```
    However, the environment variable `%win_lib%` is not defined, so these lines result in an error of the form
    ```
    The system cannot find the batch label specified - download_unzip_install
    ```
  * These errors have been reported several places since April 2020 (such as [here](https://github.com/osrf/gazebo_tutorials/issues/96)) but I could not find any solution.

  * For `ign-cmake`, `ign-math` and `ign-common` (steps 8-10) these errors did not result in a failure of `.\configure`: It appears that `cmake` is able to locate the necessary packages in the directory structure already established.

  * For `ign-fuel-tools` (step 11) the `.\configure` script failed to find several necessary packages: `IgnCURL`, `jsoncpp`, `yaml`, `libzip` and `ignition-common1`.

    * I was able to fix all but the last by adding the Gazebo workspace directory to the end of `CMAKE_PREFIX_PATH`:
      ```
      set CMAKE_PREFIX_PATH=C:/opt/ros/melodic/x64;C:/opt/rosdeps/x64;C:/opt/vcpkg/installed/x64-windows;C:/opt/gz-ws
      ```
    * I managed to get it to find `ign-common1` by explicitly setting an environment variable as specified in the error message during configuration
      ```
      set ignition-common1_DIR=c:\opt\gz-ws\ign-common\build
      ```

    * However, then configuration failed with this error
      ```
      Imported target "JSONCPP::JSONCPP" includes non-existent path
         "C:/Users/scpeters/Downloads/jsoncpp-1.8.4/install/include"
      in its INTERFACE_INCLUDE_DIRECTORIES.
      ```
      So apparently this package has issues upon issues.

    * Fortunately, `ign-fuel-tools` is not a require package for Gazebo.

  * Configuration, build and installation of `ign-msgs`, `ign-transport`, `sdformat` (steps 12-14) worked too (although there were a lot of warnings produced).

  * Configuration of `gazebo` (step 15) generated a number of warnings (including that Ignition Fuel Tools was not found and hence Fuel support will be disabled) but completed.

  * Build of `gzclient` failed during a link (at about 11%) with error
    ```
    C:\opt\rosdeps\x64\bin\libcurl.dll : fatal error LNK1107: invalid or corrupt file: cannot read at 0x300
    ```
    I am concerned that the build is accessing `rosdeps\x64\bin\` rather than `gz-ws\bin` and hence may be getting a wholly incompatible DLL.

    * At this point I gave up, and discovered that Gazebo had already been installed through `ros-melodic-desktop_full` back in M1.


