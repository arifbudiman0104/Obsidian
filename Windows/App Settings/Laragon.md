#laravel #app 
# Laragon
![[Laragon.png]]

[Laragon Documentation](https://laragon.org/docs/install.html)
[Laragon Github](https://github.com/leokhoa/laragon)
Download from [Web](https://laragon.org/download/) or [Github Release](https://github.com/leokhoa/laragon/releases)

## Installation
To start the journey with Laragon, just download from [Web](https://laragon.org/download/) or [Github Release](https://github.com/leokhoa/laragon/releases) the latest version and click Next, Next, Next...

### Setup - Welcome page

![Setup - Welcome page](https://i.imgur.com/4OyDDhK.png)

### Setup - Location

![Setup - Location](https://i.imgur.com/sJK59DC.png)

### Setup - Options

![Setup - Options](https://i.imgur.com/8oZ4N8E.png)

````ad-note
- [ ] Run Laragon when Windows starts
- [x] Auto virtual hosts
- [x] Add Notepad++ & Terminal to the Right-Click Menu
````

## Download & Config
### Composer Latest
Download composer.phar [here](https://getcomposer.org/download/)
Put downloaded composer.phar into 
```
C:\laragon\bin\composer
```

![[laragon1.png]]
### phpMyAdmin Latest
Download phpMyAdmin-XXX.zip [here](https://www.phpmyadmin.net/downloads/)
Extract, rename folder as `phpMyAdmin` and put folder into
```
C:\laragon\etc\apps
```

![[laragon2.png]]
### Git Latest
Download Git.exe [here](https://git-scm.com/downloads) and install as usual.

### PHP 7.4,8.0,8.1 x64 Thread Safe
Download PHP.zip [here](https://www.php.net/downloads.php) and extract. Put the folder into

```
C:\laragon\bin\php
```

![[laragon3.png]]
and you can change php version like this
![[laragon6.png]]

| PHP Version | Laravel Version |
|:-----------:|:---------------:|
|  7.3 - 8.1  |        8        |
|  8.0 - 8.1  |        9        |

### Node.js Windows Binary Latest
Download Node.zip [here](https://nodejs.org/en/download/) and extract. Put the folder into

```
C:\laragon\bin\nodejs
```

![[laragon4.png]]
and you can change nodejs version like this
![[laragon7.png]]
### Document Root (Optional)
- Open Laragon App
- Click `Menu` > `Preference`
- Change `Document Root` into

```
D:\Laravel
```

![[laragon5.png]]
## Windows Env
- Open Laragon App
- Click `Menu` > `Tols` > `Path` > `Add Laragon to Path`
![[laragon8.png]]
- Click `Start`
- Type `env`
- Click `Edit the system environment variables` > `Environment Variables`
- On the User Variables, click `Path` > `Edit`
- Check all the path

make sure all the path registered in windows env like this
![[laragon9.png]]