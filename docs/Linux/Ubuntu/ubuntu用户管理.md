# Ubuntu用户管理

## 1、新增用户

- 1.1 使用adduser命令，会自动为创建的用户指定主目录、系统shell版本，会在创建时输入用户密码；

```shell
> sudo adduser user
[sudo] password for liangdi: 
Adding user 'user' ...
Adding new group 'user' (1001) ...
Adding new user 'user' (1001) with group 'user' ...
Creating home directory '/home/user' ...
Copying files from '/etc/skel' ...
# 输入两次新用户的密码
New password: 
Retype new password: 
passwd: password updated successfully
Changing the user information for user
Enter the new value, or press ENTER for the default
	Full Name []: 
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] y
# 查看/home,此时已经自动创建了user文件夹
> ll
total 16
drwxr-xr-x  4 root    root    4096 Jan 24 02:10 ./
drwxr-xr-x 20 root    root    4096 Dec 17 15:00 ../
drwxr-xr-x  3 liangdi liangdi 4096 Jan 24 02:08 liangdi/
drwxr-xr-x  2 user    user    4096 Jan 24 02:10 user/
```

- 1.2 使用useradd命令，需要使用参数选项指定上述基本设置，如果不使用任何参数，则创建的用户无密码、无主目录、没有指定shell版本；

```shell
> sudo useradd -d /home/user -m -s /bin/bash user
# 设置用户密码
> sudo passwd user
New password: 
Retype new password: 
passwd: password updated successfully
# 查看/home,此时已经自动创建了user文件夹
> ll
total 16
drwxr-xr-x  4 root    root    4096 Jan 24 02:21 ./
drwxr-xr-x 20 root    root    4096 Dec 17 15:00 ../
drwxr-xr-x  3 liangdi liangdi 4096 Jan 24 02:08 liangdi/
drwxr-xr-x  2 user    user    4096 Jan 24 02:21 user/
```

## 2、修改用户相关参数

```shell
# 指定用户主目录
> sudo usermod -d /home/user user
# 指定用户命令行
> sudo usermod -s /bin/bash user
```

## 3、赋予用户管理员权限

```shell
# 编辑/etc/sudoers文件
>sudo vim /etc/sudoers
# 仿照root把用户写入root下行即可
```

## 4、删除用户

1. 使用deluser只删除用户
```shell
sudo deluser user
```

2. 使用deluser连同用户的主目录和邮箱一起删除
```shell
sudo deluser --remove-home user
```

3. 使用deluser连同用户拥有的所有文件删除
```shell
sudo deluser --remove-all-files user
```

4. 使用userdel只删除用户
```shell
sudo userdel user
```

5. userdel连同用户主目录一起删除
```shell
sudo userdel -r user
```