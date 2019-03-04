# Mima.rs

- It's a password manager using Rust, Rocket, Diesel and PostgreSQL.
- 这是一个密码管理器，采用技术：Rust, Rocket, Diesel, PostgreSQL。

## 不是网站

- 本软件虽然采用了网站框架来制作，但只是为了方便而已。
- 制作时只考虑了在本地使用的情形，未考虑联网安全，不宜联网使用。
- 这是一个单用户系统，使用时只需要输入密码，不需要输入用户名，也无法新建第二个用户。

## 安装

- 先参照 `create_role_and_database.md` 进行操作.
- 由于采用了 sodiumoxide, 因此需要设定相关的环境变量 https://crates.io/crates/sodiumoxide

## 已实现的安全措施

- 对每一条记录中的 password 和 notes 进行了有效的加密.
- 服务器端有定时关闭功能, 一旦超时立刻无法访问数据.
- 定时关闭默认为 30 分钟, 但每次有请求进入服务器, 均再次重设为 30 分钟.
- 前端网页设有自动刷新功能, 与服务器端的超时关闭功能配合, 提高安全性.
- 自动刷新默认为 30 分钟, 但每当刷新网页, 均再次重设为 30 分钟, 因此只有当停留在同一页面超过 30 分钟时才会自动刷新.
- 服务器端向前端网页返回数据时, 一律向 header 中添加了禁止缓存的设定, 因此点击浏览器的后退键也不会泄露信息.

## 特点

本程序具有以下优点，其他密码管理器大多不具备这些优点。

- 有修改历史
- 简洁模式

## 安全风险提示

- 本程序的主密码, 建议采用 12 位以上包含数字和大小写字母, 没有规律, 与个人信息 (生日, 电话号码等) 无关的密码.
- 为了进一步提高安全性, 建议临时禁用浏览器的所有插件, 并使用浏览器的无痕模式.

