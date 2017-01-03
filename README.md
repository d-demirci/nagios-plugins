# nagios-plugins
################################################################################  
To Use check_jdns file :  
copy the file to /usr/local/nagios/libexec folder or [path/to/nagios/libexec]  
make the file executable : chmod +x check_jdns  
change the owner to nagios : chown nagios:nagios check_jdns  
make sure your $USER1$ points to : /usr/local/nagios/libexec or [path/to/nagios/libexec]  
create a command in command.cfg :  
like ->  
define command {  
        command_name check_jdns  
        command_line $USER1$/check_jdns -u $ARG1$ -d $ARG2$ -e $ARG3$  
        }  
create a service in any host.cfg file <such as : windows.cfg>  
define service{  
        use			 generic-service          
        hostgroup_name	 	denizdemirci_web  
        service_description	www.denizdemirci.xyz  DNS Control JDNS  
        check_command           check_jdns!www.denizdemirci.xyz!195.175.39.39!104.27.146.199  
}  
you are all done (don't forget to define your hostgroup  )  
################################################################################  
