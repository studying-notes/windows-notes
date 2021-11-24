<!--
 * @Date: 2021.06.02 09:16:49
 * @Description: Omit
 * @LastEditors: Rustle Karl
 * @LastEditTime: 2021.11.24 15:40:34
-->

## 获取进程运行命令

```
https://superuser.com/questions/415360/how-do-i-find-out-command-line-arguments-of-a-running-program
```

### 通过软件获取

https://download.sysinternals.com/files/ProcessExplorer.zip

### 通过 wmic 获取

> 必须以管理员运行

```cmd
wmic process where caption="nutsvpn.exe" get caption,commandline,ProcessId /value
```

```
C:\Standalone\Nuts\nutsvpn.exe  -c ss://aes-256-cfb:a71b4a321118@193.112.124.22:8388 -socks 127.0.0.1:8838 -auth '15614899|14799081|eLxsrB5NpxA47SN8GXyX' -wlog '15614899|sup21760173|00:15:5D:E6:C8:06|pc|nuts|1.0.4|6859|193.112.124.22|HASEE|pc|1920*1080|windows10|10.0.19042|https://nurndtaa.com/|eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MTU2MTQ4OTksInVzZXJuYW1lIjoic3VwMjE3NjAxNzMiLCJkZXZpY2VfaWQiOjE5Njc2NjM1fQ.rVuaRMySijNk0gkKVTprxaxICqREj2u2mV9c07M-Ax8|50|600'
```

```
curl --socks5 localhost:8838 http://google.com/
```

```
curl -x localhost:8118 http://google.com/
```

```cmd
wmic process where caption="msedge.exe" get caption,commandline,ProcessId /value
```
