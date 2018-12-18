---
title: 基于PHP编写返回JSON数据的API接口
tags:
  - API
  - PHP
url: 61.html
id: 61
categories:
  - PHP
date: 2018-09-13 13:58:53
---

首先，配置PHP连接数据库的配置文件config/db.php

    <?php
    header('Content-Type: application/json');
    header('Content-Type: text/html;charset=utf8');
    $con=new mysqli("dbhost","dbuser","password","dbname");
    if(!$con){
        echo "数据库连接失败！";
        echo $con->error;
    }

其次，以下为具体实现过程：

    <?php
    require "config/db.php";
    $key=$_GET['key'];//设置API访问时的APP Key
    if($key=="XXX") {
    //验证APP Key，可以通过与数据库中保存的APP Key进行对比
        $sql = "SELECT * FROM dbtable";
        $result = $con->query($sql);
        if (!$result) {
            echo $con->error;
        } else {
            $arr = array();
            while ($row = $result->fetch_assoc()) {
                $count = count($row);//不能写到for循环里
                for ($i = 0; $i < $count; $i++) {
                    unset($row[$i]);
                }
                array_push($arr, $row);
                //将获取的$row数据压入$arr数组中
            }
            print_r($arr);
            echo "<br/><hr>";
            echo json_encode($arr,JSON_UNESCAPED_UNICODE);
            echo "<br/>";
            $con->close();
        }
    }else{//APP Key验证不通过所返回的输出
        ...
    }

此处仅输出了返回的JSON格式数据，可根据自己的需要输出返回状态码。