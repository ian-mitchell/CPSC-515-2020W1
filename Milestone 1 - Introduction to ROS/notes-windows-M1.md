# Notes from running CPSC 515 M1 (2020W1 edition) in Windows 10

Find instructions for the milestone at [class GitHub repository](https://github.com/ian-mitchell/CPSC-515-2020W1/blob/M1/Milestone%201%20-%20Introduction%20to%20ROS/M1.md).

* Windows install went smoothly for the most part.  
  * Did not have to adjust virus scanner or manually install `vcpkg`.
  * Adjusting the start directory of command window shortcut.  The "start in" folder is essentially ignored when you set a shortcut to run as Administrator (see [here](https://superuser.com/questions/1067901/how-to-open-command-prompt-in-a-specific-folder-as-administrator)).  Instead, adjust the command line to manually cd into the desired directory at the end.  I chose to add `&& cd C:\opt` to the end of the recommended command string.  In general could also pass `/k cd C:\opt` to `cmd.exe` if the `/k` flag wasn't already being used to run a batch file in this case.
* Problem running `catkin_make` because I also have Cygwin installed on my machine.  Apparently the `cygwin64` python executable was being used instead of the one in `opt/` (likely path ordering issue).  Explicitly specifying the python executable seemed to work:

    ```catkin_make -DPYTHON_EXECUTABLE=C:\opt\python27amd64\python```

* Tutorials are Linux / bash focused.  For Windows some adjustments need to be made:
  * There is no `source` command in Windows.  To execute a batch file, just enter a full directory path (including `.\` if necessary) at the command prompt.  For example, in tutorial 1.1.1.3, instead of `source devel\setup.bash` it would be `devel\setup.bat` (or `.\devel\setup.bat`).
  * Instead of `echo $ENV_VARIABLE_NAME` in bash, use `echo %ENV_VARIABLE_NAME%`.
  * Instead of `sudo apt-get install <ros-pkg>` use `choco install --name=<ros-pkg> --source="https://aka.ms/ros/public" --priority=1`.
  * ROS tab completion (tutorial 1.1.2.3.5) does not appear to work in the Windows shell.  (Regular command line tab completion works if you use `\` (backslash) as your directory separator.)
  * Assuming that you set up the command window shortcut during installation and are using it, then you don't need to source your environment setup again, such as mentioned in tutorial 1.1.4.1.
  * When you run `roscore` you will probably need to permit network access through Windows Firewall.  Same thing will happen the first time you start other nodes.
  * When killing nodes, kill the executable (such as by closing the turtlesim window in tutorial 1.1.5.7).  If you just press `ctrl-C` in the terminal window where you launched the node, roscore won't know it is gone.  If you have zombie node names showing in `rosnode list`, you can use `rosnode cleanup` to tidy them up.  (I haven't tried setting `ROS_HOSTNAME=localhost` and `ROS_MASTER_URI=http://localhost:11311` as described in item 2.2 of [ROS/NetworkSetup](https://wiki.ros.org/ROS/NetworkSetup#Single_machine_configuration) because I don't want to wrestle with ROS networking in Windows yet.  Let me know if you do try it.)
  * For `rqt_graph` and other commands which pop up a window, the empty grey rectangles in the window are actually buttons.  Mouse over them to see what they do.  For example, the empty grey rectangle in the top left of the `rqt_graph` window is the "Refresh ROS graph" button (which you will use frequently).
  * When putting command line parameters inside quotes, use double quotes `"` not single quotes `'`.  For example, for `rostopic pub` in tutorial 1.1.6.4.1 instead of 
    ```
    rostopic pub -1 /turtle1/cmd_vel geometry_msgs/Twist -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]'
    ``` 
    use 
    ```
    rostopic pub -1 /turtle1/cmd_vel geometry_msgs/Twist -- "[2.0, 0.0, 0.0]" "[0.0, 0.0, 1.8]"
    ``` 
    Or if you want to use the full YAML dictionary notation for specifying the data:
    ```
    rostopic pub -1 /turtle1/cmd_vel geometry_msgs/Twist -- "{linear:  {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0, z: 1.8}}"
    ```
  * It was not part of the milestone, but it appears that the `rosed` command is not defined.  But perhaps I did not set my `EDITOR` environment variable correctly.
  * Tutorial 1.1.12 puts the Python `talker.py` and `listener.py` scripts into a subdirectory of `beginner_tutorials` called `scripts/` (in other words `catkin_ws\src\beginner_tutorials\scripts\`).  It appears that `rosrun` cannot find them there unless you specify the subdirectory when naming the executable, for example, `rosrun beginner_tutorials scripts\talker.py`.  This behaviour stands in contrast to the executables generated for C++ code.
    * Python scripts can be found by `rosrun` if you do `catkin_make install` and then `install\setup.bat`.  Getting this process to work correctly is apparently the purpose of the `catkin_install_python()` call in `CMakeLists.txt` (see [here](http://docs.ros.org/melodic/api/catkin/html/howto/format2/installing_python.html)).  But then the script which is executed is a copy from the `catkin_ws\install` directory tree, so changes to the scripts in `src\` will not be visible.
    * Not clear if this is a Windows specific problem or not.  It was [asked on ROSanswers](https://answers.ros.org/question/326072/windows10-rosrun-couldnt-find-python-scripts-in-path-scripts/) but there is not currently an obvious answer.