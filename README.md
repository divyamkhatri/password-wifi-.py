# password-wifi-.py
import subprocess                                                                           #made by divyam                                                                                     
import re
      
command_output=subprocess.run(["netsh","wlan","show","profiles"],capture_output=True).stdout.decode()

profile_name=(re.findall("All User Profile     : (.*)\r",command_output))
wifi_dictionary={}
                                                                                            #class 11
for name in profile_name:

   profile_info=subprocess.run(["netsh","wlan","show","profile",name,"key=clear"],capture_output=True).stdout.decode()

   password=(re.findall("Key Content            : (.*)\r",profile_info))
   for passw in password:
      wifi_dictionary[name]=passw
print(wifi_dictionary)
