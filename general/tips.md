#### SSH Key Generation

1. Cmd ortamından bash durumuna geçilir
2. Ardından command prompt'a aşağıdaki kod yazılır ve gerekli ssh elde edilir.
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

#### Software Quality Check 
The Joel Test

1. Do you use source control?
2. Can you make a build in one step?
3. Do you make daily builds?
4. Do you have a bug database?
5. Do you fix bugs before writing new code?
6. Do you have an up-to-date schedule?
7. Do you have a spec?
8. Do programmers have quiet working conditions?
9. Do you use the best tools money can buy?
10. Do you have testers?
11. Do new candidates write code during their interview?
12. Do you do hallway usability testing?

#### Adding new Open With 

`regedit` in command line
go to -> **_HKEY_CLASSES_ROOT > * > shell_**
add new key **_Open with x_**
add new key inside that **_Command_**
and value is **"C:\Program Files (x86)\Notepad++\notepad++.exe" "%1"**
