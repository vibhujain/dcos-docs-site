---
layout: layout.pug
navigationTitle:  连接 
title: 连接 
menuWeight: 1
excerpt: 配置与 LDAP 服务器的连接 
render: mustache
model: /mesosphere/dcos/1.13/data.yml
enterprise: true
---

在本部分中，您将指定用于连接到 LDAP 服务器的地址、协议和证书。

1. 单击 **Settings** -> **LDAP Directory** 选项卡。

1. 单击 **Add Directory**。

   ![添加目录对话框](/mesosphere/dcos/1.13/img/ldap-add-dir-conn.png)

   图 1. 添加目录对话框

1. 在 **Host** 框中键入 LDAP 目录服务器的主机名或 IP 地址。不要包含协议前缀或端口号。

1. 键入要在 **Port** 框中使用的 TCP/IP 端口号。端口 `389` 通常用于 StartTLS 和未加密通信。端口 `636` 通常用于 LDAPS 连接。

1. 从 **Select SSL/TLS setting** 列表框中选择首选加密选项。

    * 选中 **对所有连接使用 SSL/TLS ** 以使用[安全 LDAP（LDAPS）](http://social.technet.microsoft.com/wiki/contents/articles/2980.ldap-over-ssl-ldaps-certificate.aspx)。

    * 如果**尝试 StartTLS，如果未能**尝试通过 [StartTLS](https://tools.ietf.org/html/rfc2830) 将连接升级到 TLS，则中止，如果升级到 TLS 失败，则中止连接。

    * 如果**尝试 StartTLS，如果未能**尝试通过 [StartTLS](https://tools.ietf.org/html/rfc2830) 将连接升级到 TLS，则继续不加密，如果升级到 TLS 失败，则继续不加密连接。

   <p class="message--note"><strong>注意：</strong>我们建议选择<strong>为所有连接选择 SSL/TLS</strong>或<strong>尝试 StartTLS，如果失败则中止 </strong> 以确保 SSL/TLS 或 StartTLS 加密；否则密码将以明文形式发送。</p>

1. 如果 LDAP 目录服务器要求 DC/OS 提供[客户端证书](https://tools.ietf.org/html/rfc5246#section-7.4.6)，请将其粘贴到 **Client certificate and private key (Optional)** 字段。值应类似于以下内容。

    ```
    -----BEGIN PRIVATE KEY-----
    MIIDtDCCApy...
    -----END PRIVATE KEY-----
    -----BEGIN CERTIFICATE-----
    OIymBpP...
    -----END CERTIFICATE-----
    ```

1. 要确保 DC/OS 群集不接受来自指定 LDAP 目录服务器以外的其他方的连接，请将 LDAP 目录服务器的根 CA 证书和任何中间证书粘贴到 **CA certificate chain (Optional)** 字段中。我们强烈建议您完成此步骤，以便与 LDAP 目录服务器建立安全通信信道。

1. 指定身份认证方法和参数，如[身份认证部分](/mesosphere/dcos/cn/1.13/security/ent/ldap/ldap-auth/)中所述。
