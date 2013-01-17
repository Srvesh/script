script
======

Menu script is given below.

How to run?

copy and paste and give the 755 permission to execute this script.


      #!/bin/bash
      while :

      do
      clear
      echo  " ***welcome to the Menu script*** "
      echo  "Please choose from the followings"
      echo  "1. Change Password"
      echo  "2. See the disk space"
      echo  "3. Login to other box using ssh"
      echo  "4. Show all Service running"
      echo  "5. Show all ports opened"
      echo  "6. Show all java apps running"
      echo  "7. Facility to kill a  app"
      echo  "8. Exit"
      echo -n "please enter the choice [1 - 8]"
      read option
      
      case $option in 
       
       1) echo "please enter the new password";
        passwd 
        read enterKey;;
   
        2) echo "please wait....";
        #df ;
        #df -m ;
        df -h ;
        echo "Press a key. . ." ; read -n 1 ;; 
      
        3) echo "you have choose option $option... please enter the IP of the server, which you want to SSH";
        read ip 
        /usr/bin/ssh root@${ip};
        echo "Press a key. . ." ; read -n 1 ;;
        
        4) echo "please wait .....";
        service --status-all;
        chkconfig --list |grep on;
        echo "Press a key. . ." ; read -n 1 ;;

        5) echo "here is the list of all open ports on your server, it can be done by two methods, 1 netstat and 2 lsof ";
         netstat -nap;
         echo "lsof";
         lsof -i -n -P;
         echo "Press a key. . ." ; read -n 1 ;;  
        
        6) echo "Java process"
        ps -ef  |grep java;
        echo "Press a key. . ." ; read -n 1 ;;
 
        7) echo "please enter the PID to kill :"
        read pid;
        kill -9 $pid;
        echo "$pid killed"
        echo "Press a key. . ." ; read -n 1 ;;
        
        8) echo "Exiting the Menu" 
        exit;;
  
        *) echo "$option is invalid option. Please select between 1 to 8 only"
        echo "Press [enter] key to continue. . .";
        read enterkey;;
     esac
    done
