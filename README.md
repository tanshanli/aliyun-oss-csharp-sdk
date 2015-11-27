﻿# Aliyun OSS SDK for .NET
## 关于
> - 此.NET SDK基于[阿里云对象存储服务](http://www.aliyun.com/product/oss/)官方API构建。
> - 阿里云对象存储（Object Storage Service，简称OSS），是阿里云对外提供的海量，安全，低成本，高可靠的云存储服务。
> - OSS适合存放任意文件类型，适合各种网站、开发企业及开发者使用。
> - 使用此SDK，用户可以方便地在任何应用、任何时间、任何地点上传，下载和管理数据。

## 版本
> 当前版本：2.1.0

## 运行环境
> - 适用于`.NET 2.0` 及以上版本
> - 适用于`Visual Studio 2010`及以上版本

## 安装方法
### NuGet安装
> - 如果您的Visual Studio没有安装NuGet，请先安装 [NuGet](http://docs.nuget.org/docs/start-here/installing-nuget).
> - 安装好NuGet后，先在`Visual Studio`中新建或者打开已有的项目，然后选择`<工具>`－`<NuGet程序包管理器>`－`<管理解决方案的NuGet程序包>`，
> - 搜索`aliyun.oss.sdk`，在结果中找到`Aliyun.OSS.SDK`，选择最新版本，点击安装，成功后添加到项目应用中。

### DLL引用方式安装
> - 从阿里云官网下载SDK包，解压后bin目录包括了Aliyun.OSS.dll文件。
> - 在Visual Studio的`<解决方案资源管理器>`中选择您的项目，然后右键`<项目名称>`-`<引用>`，在弹出的菜单中选择`<添加引用>`.
在弹出`<添加引用>`对话框后，选择`<浏览>`，找到sdk包解压的目录，在bin目录下选中`<Aliyun.OSS.dll>`文件,点击确定即可

### 项目引入方式安装
> - 如果是下载了SDK包或者从github上下载了源码，希望源码安装，可以右键`<解决方案>`，在弹出的菜单中点击`<添加>`->`<现有项目>`.
> - 在弹出的对话框中选择`aliyun-oss-sdk.csproj`文件，点击打开。
> - 接下来右键`<您的项目>`－`<引用>`，选择`<添加引用>`，在弹出的对话框选择`<项目>`选项卡后选中`aliyun-oss-sdk`项目，点击确定即可。

## 快速使用
#### 获取存储空间列表（List Bucket）
```csharp
    OssClient client = new OssClient(endpoint, accessId, accessKey);    
	var buckets = client.ListBuckets();
	
    foreach (var bucket in buckets)
    {
    	Console.WriteLine(bucket.Name + ", " + bucket.Location + ", " + bucket.Owner);
    }
```
    
#### 创建存储空间（Create Bucket）
```csharp
	OssClient client = new OssClient(endpoint, accessId, accessKey);
	client.CreateBucket(bucketName);
```
	
#### 删除存储空间（Delete Bucket）
```csharp
	OssClient client = new OssClient(endpoint, accessId, accessKey); 
	client.DeleteBucket(bucketName);
```

#### 上传文件（Put Object）
```csharp
	OssClient client = new OssClient(endpoint, accessId, accessKey); 
	client.PutObject(bucketName, key, filePathToUpload);
```

#### 下载文件 (Get Object)
```csharp
	OssClient client = new OssClient(endpoint, accessId, accessKey); 
	var object = ossClient.GetObject(bucketName, key);	
```

#### 获取文件列表（List Objects）
```csharp
	OssClient client = new OssClient(endpoint, accessId, accessKey);
	var listResult = client.ListObjects(bucketName);
	foreach (var summary in listResult.ObjectSummaries)
	{   
		Console.WriteLine(summary.Key);
	}
```
	
#### 删除文件(Delete Object)
```csharp
	OssClient client = new OssClient(endpoint, accessId, accessKey);
	client.DeleteObject(bucketName, key)
```

#### 其他
    更详细的例子可以在aliyun-oss-sample项目中查看并运行
	
## 注意事项
> - 如果要运行sample，需要将aliyun-oss-sdk-sample项目设为`启动项目`，并添加您自己的AccessKeyId，AccessKeySecret，bucket，key等后即可运行。

## 联系我们
- [阿里云OSS官方网站](http://oss.aliyun.com)
- [阿里云OSS官方论坛](http://bbs.aliyun.com)
- [阿里云OSS官方文档中心](http://www.aliyun.com/product/oss#Docs)
- 阿里云官方技术支持：[提交工单](https://workorder.console.aliyun.com/#/ticket/createIndex)