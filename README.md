TubeTK Dashboard Scripts
========================

This is a directory of the files that control TubeTK's dashboard machines. These files are updated and run on the dashboard client machines every night.

Assumptions
-----------

1. The top level of your dashboard directory is `/home/me/src/dashboards`.
2. The machine's name is `MyMachine`.

Commands
--------

Go to the top level of your dashboard clients.

    $ cd /home/me/src/dashboards

Get a copy of all the dashboard scripts from the Git repository, including some example scripts.

    $ git clone https://github.com/TubeTK/TubeTK-DashboardScripts.git

This is the script that will update and launch your dashboard client every night. Use the `.bat` file if you are doing this on Microsoft Windows.

    $ cd TubeTK-DashboardScripts
    $ cp EXAMPLE_TubeTK_Nightly.sh MyMachine_TubeTK_Nightly.sh

Setup your machine's parameters as described in the file.

    $ vi MyMachine_TubeTK_Nightly.sh

By adding your script to the Git repository, your dashboard machine can be updated without having to log into it.

    $ git add MyMachine_TubeTK_Nightly.sh
    $ git commit -m "ENH: Initial setup shell for MyMachine"

Make sure you have the latest copy of the `TubeTK-DashboardScripts` directory and then submit your changes to the Git repository.

    $ git pull
    $ git push

The MyMachine_TubeTK_Nightly.sh script must reside outside of the `TubeTK-DashboardScripts` directory so that it can be updated as it is run.  So copy it up one level.  That copy is the version which must be run every night.

    $ cp MyMachine_TubeTK_Nightly.sh ..

Do this on Linux machines to setup a recurring nightly job.
Create a specific set of parameters for your dashboard machine.

    $ cd TubeTK-DashboardScripts
    $ cp EXAMPLE_Linux.cmake MyMachine_TubeTK.cmake

Setup the parameters as specified in that file.

    $ vi MyMachine_TubeTK.cmake

By adding your script to the Git repository, your dashboard machine can be updated without having to log into it.

    $ git add MyMachine_TubeTK.cmake
    $ git commit -m "ENH: Initial setup for MyMachine"

Make sure you have the latest copy of the `TubeTK-DashboardScripts` directory and then submit your changes to the Git repository.

    $ git pull
    $ git push

Do this on Linux machines to setup a recurring nightly job.

    $ crontab -e

Add the following line to run your copy of the script outside of the dashboard repository.  Please change the start minute (20) and the start hour (0) to different values to avoid simultaneous downloads from multiple machines.

    20 0 * * * /home/me/src/dashboards/MyMachine_TubeTK_Nightly.sh

On Microsoft Windows, use the task scheduler to run your `MyMachine_TubeTK_Nightly.bat` script.

---
*This file is part of [TubeTK](http://www.tubetk.org). TubeTK is developed by [Kitware, Inc.](http://www.kitware.com) and licensed under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0).*
