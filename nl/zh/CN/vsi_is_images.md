---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# 映像
{: #images}

供应 {{site.data.keyword.vsi_is_full}} 时，可从支持的库存映像中进行选择。选择的映像将确定为实例供应的操作系统。
{:shortdesc}

## 库存映像
{: #stock-images}

创建虚拟服务器时，以下操作系统作为库存映像提供。
* CentOS 7.x
* Debian 8.x 和 9.x
* Red Hat Enterprise Linux 7.x
* Ubuntu 16.04 和 18.04
* Windows 2012、2012 R2 和 2016

订购实例时，映像已启用 cloud-init 以优化供应时间。通过启用了 cloud-init 的映像，可以提供用户数据。在订购表单上的**用户数据**字段中，可以输入服务器的可选 cloud-init 用户数据。有关用户数据和自动化的更多信息，请参阅[用户数据](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-user-data#user-data)。

## 虚拟化
{: #virtualization}
实例需要支持硬件虚拟化机器 (HVM) 引导方式的映像。HVM 虚拟化类型允许映像直接在虚拟服务器上运行，这对于高级联网和 GPU 功能是必需的。
