---
title: Trojan protocol
layout: default
nav_order: 13
---

<p dir="rtl">
این روش برای مستقیم هست و نیاز به سرور ایران نداره ؛ باهاش میتونید کانفیگ تروجان بسازید ولی خوب این با تروجانی که روی هسته های دیگه میسازید فرق خواهد کرد
</p>

<p dir="rtl">
شما درحال حاضرنیازی به تغییر سمت کلاینت ندارید ؛ روی تمام برنامه های v2ray اجرا میشه
</p>

<p dir="rtl">
و در عین حال تغییراتش همینطور پیش میرن تا هم روی ایرانسل و هم روی همراه به هیچ وجه فیلتر نشه
</p>

<p dir="rtl">
درحال حاضر مهم ترین تغییرش این بوده که جولوی tls in tls مقاوم شده و با trojan-killer دیتکت نمیشه
</p>

<p dir="rtl">
دوستانی که میخوان تست کنن با اجرای این کانفیگ در سرور خارج ؛ روی پورت ۴۴۳ میتونن اجرا کنن
</p>

<p dir="rtl">
کلا یه اکانت تروجان  فرض شده با رمز 1234
</p>

<p dir="rtl">
وضعیت فیلترینگ:
</p>

<p dir="rtl">
فتغییرات در اپدیت 1.20 برای تست قرار داده شد ؛‌ فعلا 4 روزه که مشکلی پیش نیومده
</p>


* * *

<p dir="rtl">
دقت کنید فایل های سرتیفکیت لازم هستند
</p>

<p dir="rtl">
و همچنین فالبک http رو بهتره به وبسایت خودتون یا جا های رندوم دیگه بدید
</p>

<p dir="rtl">
احتمال اینکه این فالبک رو حساس کرده باشن مقداری وجود داره 
</p>

<p dir="rtl">
پیشنهاد میشه که 
روی کانفیگ کلاینت که میخواید استفاده کنید alpn رو برابر با h2 یا http/1.1 قرار بدید 
</p>



```json
{
    "name": "direct_trojan",
    "nodes": [
        {
            "name": "my-tcp-listener",
            "type": "TcpListener",
            "settings": {
                "address": "0.0.0.0",
                "port": 443,
                "nodelay": true
            },
            "next": "my-ssl-server"
        },
        {
            "name": "my-ssl-server",
            "type": "OpenSSLServer",
            "settings": {
                "anti-tls-in-tls":true,
                "cert-file": "fullchain.pem",
                "key-file": "privkey.pem",
                "alpns": [
                    {
                        "value": "h2",
                        "next": "node->next"
                    },
                    {
                        "value": "http/1.1",
                        "next": "node->next"
                    }
                ],
                "fallback":"my-tls-fallback"

            },
            "next": "my-trojan-auth"
        },
        {
            "name": "my-trojan-auth",
            "type": "TrojanAuthServer",
            "settings": {
                "fallback":"my-trojan-fallback",
                "fallback-intence-delay":200,

                "users": [
                    {
                        "name": "sample_user",
                        "uid": "1234",
                        "enable": true
                    }
                ]
            },
            "next": "my-trojan-socks"
        },
        {
            "name": "my-trojan-socks",
            "type": "TrojanSocksServer",
            "settings": {},
            "next": "my-connector"
        },
        {
            "name": "my-connector",
            "type": "Connector",
            "settings": {
                "nodelay": true,
                "address":"dest_context->address",
                "port":"dest_context->port"
            }
        },
        {
            "name": "my-tls-fallback",
            "type": "TcpConnector",
            "settings": {
                "nodelay": true,
                "address":"demo.nginx.com",
                "port":443
            }
        },
        {
            "name": "my-trojan-fallback",
            "type": "TcpConnector",
            "settings": {
                "nodelay": true,
                "address":"httpforever.com",
                "port":80
            }
        }
    ]
}
```


<p dir="rtl">
توضیحات کامل تر میشه همینطور که پروژه پیش میره ولی تا جایی که میدونم با نگاه کردن به خود json تا حد خیلی خوبی میشه فهمید چی به چیه
</p>


[Homepage](.) | [Prev Page](Bgp4-Tunnel-or-Direct) | [Next Page](HalfDuplex-Tunnel-or-Direc)
