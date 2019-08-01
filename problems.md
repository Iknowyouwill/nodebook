## 1. 在linux上执行npm install, node-sass安装报错, 
```
Unable to save binary /data/wwwroot/default/teacher-admin-master/node_modules/node-sass/vendor/linux-x64-59 : 
{ Error: EACCES: permission denied, mkdir '/data/wwwroot/default/teacher-admin-master/node_modules/node-sass/vendor'
```
解决方法:
```
npm install node-sass unsafe-perm --save-dev
```
原因:
> ## Linux
> This can happen if you are install ```node-sass``` as **root**, or globally with **sudo**. This is a security feature of npm. 
> You should always avoid running npm as sudo because install scripts can be unintentionally malicious. 
> Please check npm documentation on fixing permissions.
> If you must however, you can work around this error by using the ```--unsafe-perm``` flag with npm install i.e.
> ```$ sudo npm install --unsafe-perm -g node-sass```
>
> If this didn't solve your problem please open an issue with the output from our debugging script.

大概意思就是在用root 或者 sudo安装node-sass时会发生这种情况, 说是由于安全的考虑(不懂, 听着就对了);
所以解决方法就是添加 ```--unsafe-perm```
但是我在按上面试验的时候全局安装会失败, 去掉```-g```安装才可以.

