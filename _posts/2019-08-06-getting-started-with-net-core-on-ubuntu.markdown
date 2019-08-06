---
layout: post
title:  "Getting started with .NET Core on Ubuntu - Installing the SDK"
date:   2019-08-06 15:26:16 +0500
categories: api-gateway
---

## What is .NET Core?
.NET Core is general-purpose development framework developed and maintained by Microsoft. It is open-source and cross-platform which means it is compatible with Linux , Mac and Windows environments. 

.NET Core 1.0 was released in 2016 and the latest version running now a days is .NET Core 3.0 which is available as a preview version but will be released officially this year.

## Installing .NET Core SDK on Ubuntu

Follow the steps below to install the .NET Core SDK 

Open a terminal and run the following commands

```
wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
```
```
sudo dpkg -i packages-microsoft-prod.deb
```

## Install the .NET SDK

Run the following commands in your terminal

```
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-2.2
```

If you receive an error message `Unable to locate package dotnet-sdk-2.2,` run the following commands

```
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install dotnet-sdk-2.2
```
If you still get the same error again, try manually installing the SDK using the commands below

```
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-2.2
```

## Confirm your installation

After the installation process completes successfully, we need to make sure that we have successfully installed the .NET Core SDK.

To do that , open up your terminal and run the following command.

```
$ > dotnet --info
```
If you see response similar to the one below, congratulation! you have done it.

```
.NET Core SDK (reflecting any global.json):
 Version:   2.2.401
 Commit:    729b316c13

Runtime Environment:
 OS Name:     ubuntu
 OS Version:  19.04
 OS Platform: Linux
 RID:         ubuntu.19.04-x64
 Base Path:   /usr/share/dotnet/sdk/2.2.401/

Host (useful for support):
  Version: 2.2.6
  Commit:  7dac9b1b51

.NET Core SDKs installed:
  2.2.401 [/usr/share/dotnet/sdk]

.NET Core runtimes installed:
  Microsoft.AspNetCore.All 2.2.6 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
  Microsoft.AspNetCore.App 2.2.6 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
  Microsoft.NETCore.App 2.2.6 [/usr/share/dotnet/shared/Microsoft.NETCore.App]

To install additional .NET Core runtimes or SDKs:
  https://aka.ms/dotnet-download

```