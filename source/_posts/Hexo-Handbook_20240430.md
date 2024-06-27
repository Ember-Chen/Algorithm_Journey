---
title: Hexo Handbook
date: 2024-04-30 13:58:59
category: Handbook
---

- 为每个.md文件创建单独资源文件夹
    
    - 文件`_config.yml`中的`post_asset_folder`设置为`true`
- 并列分类
    ```
    categories:
    - [Linux]
    - [Tools]
    ```
- 并列分类+子分类
    ```
    categories:
    - [Linux, Hexo]
    - [Tools, PHP]
    ```
- 修改categories界面的层级缩进距离
    - 打开文件`/themes/next/source/css/_common/component/pages/categories.styl`
    - 修改`.category-list-item`
