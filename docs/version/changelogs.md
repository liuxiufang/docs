---
title: 版本更新记录
---

# 版本更新记录

## 2021年2月5日
* 【需求】Docker-compose 安装视频 [https://www.bilibili.com/video/BV1Dy4y1n77N/](https://www.bilibili.com/video/BV1Dy4y1n77N/)
* 【优化】修复cache的PSR-16的不规范使用
* 【优化】群公告字段问题
* 【优化】修复file的psr规范，支持阿里云、本地、腾讯，默认本地。优化其它代码调用外的读取。添加测试代码
* 【优化】添加通讯录、客户同步时，头像检测 + 坏图片重传的定时检测
* 【需求】聊天侧边栏（配置）的静态页面的引导优化
* 【需求】聊天侧边栏应用的添加、添加的即时同步、定时同步
* 【优化】docker镜像[mochat/mochat:v1]的APP_ENV变量移除
* 其他优化

### 此次更新引导
升级SQL

```sql
ALTER TABLE `mc_work_agent` ADD COLUMN `type` TINYINT ( 4 ) NOT NULL COMMENT '应用类型 1-侧边栏 2-会话消息 3-工作台' AFTER `home_url`;
ALTER TABLE `mc_corp` ADD COLUMN `tenant_id` INT(11) DEFAULT '0' COMMENT '租户ID';
ALTER TABLE mc_work_room MODIFY COLUMN notice text NOT NULL COMMENT '群公告';
INSERT INTO `mc_rbac_menu` (`parent_id`, `name`, `level`, `path`, `icon`, `status`, `link_type`, `is_page_menu`, `link_url`, `data_permission`, `operate_id`, `operate_name`, `sort`, `created_at`, `updated_at`, `deleted_at`) VALUES (71, '用户画像', 3, '#1#-#71#-#220#', '', 1, 1, 1, '/chatTool/customer', 2, 1, '', 99, '2021-02-05 11:35:55', '2021-02-05 11:35:55', NULL);
INSERT INTO `mc_rbac_menu` (`parent_id`, `name`, `level`, `path`, `icon`, `status`, `link_type`, `is_page_menu`, `link_url`, `data_permission`, `operate_id`, `operate_name`, `sort`, `created_at`, `updated_at`, `deleted_at`) VALUES (71, '聊天增强', 3, '#1#-#71#-#221#', '', 1, 1, 1, '/chatTool/enhance', 2, 1, '', 99, '2021-02-05 11:36:44', '2021-02-05 11:36:45', NULL);
INSERT INTO `mc_rbac_menu` (`parent_id`, `name`, `level`, `path`, `icon`, `status`, `link_type`, `is_page_menu`, `link_url`, `data_permission`, `operate_id`, `operate_name`, `sort`, `created_at`, `updated_at`, `deleted_at`) VALUES (14, '用户搜索添加', 3, '#1#-#14#-#222#', '', 1, 1, 1, '/greeting/userSearch', 2, 1, '', 99, '2021-02-05 11:38:10', '2021-02-05 11:38:10', NULL);
UPDATE mc_rbac_menu SET `name` = CONCAT(`name`,'(废弃)') WHERE link_url IN ('/chatTool/config', '/chatTool/config@upload');
```

后端PHP包升级
```bash
composer update mochat/framework
```

前端NGINX配置添加
```nginx
location ~ .*\.txt {
	## 后端接口
    proxy_pass http://backend.test;
 }
 ```

## 2021年1月29日
* 【功能添加】docker-compose快速安装文档、视频完成 （https://github.com/mochat-cloud/docker-compose）
* 【代码完善】添加memory_limit默认
* 【代码完善】增加https 图表优化
* 【代码完善】解禁超管功能：允许少部分操作企业数据
* 【代码完善】修复获取登录用户信息响应数据用户头像、头像缩略图地址错误的问题
* 【代码完善】mochat.sql文件字段长度调整
* 【代码完善】framework中jwt添加动态路由的白名单支持
* 【BUG修复】超级管理员不属于任何企业时，授信列表、用户列表报错的问题
* 【BUG修复】批量更新图片网络超时问题；DEV模式下客户同步失败问题；客户协程同步try...catch时变量未初始化
* 【BUG修复】新增菜单和编辑菜单，去掉选择企业限制
* 【文档修改】文档完善
* 【BUG修复】其它若干小BUG的修复

## 2021年1月18日
* MoChat 正式发布