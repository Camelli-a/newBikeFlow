# Backend使用说明

## 简要说明
backend部分 是一个基于 Node.js 的后端应用程序，旨在根据需求为前端提供相关 API。该项目使用 Express 框架构建，并集成了 MySQL 数据库。

## 安装依赖
1. 安装 Node.js 和 npm
   - 请参考 [Node.js 官网](https://nodejs.org/) 下载并安装最新版本的 Node.js。
2. 安装依赖（这一步最好在系统cmd中以管理员身份运行）
    切换到项目目录下的 `BikeFlow/backend` 文件夹，并使用 npm 安装所需的依赖包。
   ```bash
    cd BikeFlow/backend
    npm install
    ```
3. 启动app.js（在VScode的集成终端运行即可）
    ```bash
     node app.js
     ```
    若终端显示🚀 Server is running at http://localhost:${PORT}，则说明后端启动成功。
    由于当前搭建了与数据库进行连接的框架，因此我假定连接的数据库账号为root，密码为root，数据库名为schedule，具体配置在db/dbUtils.js。若出现“数据库连接失败的问题”，可以将其中的内容改为自己本地存在的某个数据库即可。
4. 结束进程
   - 在终端中按 `Ctrl + C` 结束当前进程。

## 接口说明
1.登陆注册
（1）用户注册（POST）
```bash
/admin/register
```
请求格式
```bash
{
  "username": "admin", //用户名
  "password": "admin", //密码
}
```
返回格式
```bash
{
  "code": 200, //状态码
  "msg": "注册成功"
}
```
（2）用户登录（POST）
```bash
/admin/login
```
请求格式
```bash
{
  "username": "admin", //用户名
  "password": "admin" //密码
}
```

返回格式
```bash
{
  "code": 200, //状态码
  "msg": "登录成功",
  "data": 
    {
      "account": "admin",
      "password": "",
      "token": "b8aeb113-f7b0-47ab-a373-b8719888bcf0",
      "email": null
    }
}

```
2.站点位置  
（1）获取所有的站点位置（GET）
```bash
/stations/locations
```
返回格式
```bash
{
    "station_id": "JC019",//站点编号
    "station_name": "Hilltop",//站点名
    "latitude": 40.7312,//纬度
    "longitude": -74.0576//精度
  },
  {
    "station_id": "JC024",
    "station_name": "Pershing Field",
    "latitude": 40.7427,
    "longitude": -74.0518
  },
  // ... more stations
```