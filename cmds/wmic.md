<!--
 * @Date: 2021.06.02 09:16:49
 * @Description: Omit
 * @LastEditors: Rustle Karl
 * @LastEditTime: 2021.06.24 08:47:44
-->

https://superuser.com/questions/415360/how-do-i-find-out-command-line-arguments-of-a-running-program

管理员权限

```cmd
wmic process where caption="nutsvpn.exe" get caption,commandline,ProcessId /value
```

https://download.sysinternals.com/files/ProcessExplorer.zip

C:\Standalone\Nuts\nutsvpn.exe  -c ss://aes-256-cfb:a71b4a321118@193.112.124.22:8388 -socks 127.0.0.1:8838 -auth '15614899|14799081|eLxsrB5NpxA47SN8GXyX' -wlog '15614899|sup21760173|00:15:5D:E6:C8:06|pc|nuts|1.0.4|6859|193.112.124.22|HASEE|pc|1920*1080|windows10|10.0.19042|https://nurndtaa.com/|eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MTU2MTQ4OTksInVzZXJuYW1lIjoic3VwMjE3NjAxNzMiLCJkZXZpY2VfaWQiOjE5Njc2NjM1fQ.rVuaRMySijNk0gkKVTprxaxICqREj2u2mV9c07M-Ax8|50|600'

C:\Standalone\Nuts\nutsregproxy.exe

curl --socks5 localhost:8838 http://google.com/
curl -x localhost:8118 http://google.com/
