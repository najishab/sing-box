# نحوه اعمال این پچ روی فورک najishab/sing-box

## ۱. کلون فورک خودت
```
cd C:\Users\najis\Desktop
git clone https://github.com/najishab/sing-box.git
```

## ۲. کپی فایل‌های این پچ
محتوای این پوشه (`transport/`, `protocol/`, `option/`, `common/`, `include/`) را روی همون مسیرها
داخل `C:\Users\najis\Desktop\sing-box` کپی/جایگزین کن (فایل‌های جدید اضافه می‌شن، هیچ فایل موجودی بازنویسی نمی‌شه چون
همه‌شون جدید هستن به‌جز دو مورد زیر که باید دستی ویرایش کنی).

## ۳. ویرایش دستی فایل ۱: `constant/proxy.go`
این خط رو:
```go
	TypeSSMAPI       = "ssm-api"
```
این‌جوری کن (یک خط زیرش اضافه کن):
```go
	TypeSSMAPI       = "ssm-api"
	TypeOpenVPN      = "openvpn"
```

## ۴. ویرایش دستی فایل ۲: `include/registry.go`
داخل تابع `OutboundRegistry()`، این خط رو:
```go
	registerQUICOutbounds(registry)
	registerWireGuardOutbound(registry)
```
این‌جوری کن:
```go
	registerQUICOutbounds(registry)
	registerWireGuardOutbound(registry)
	registerOpenVPNOutbound(registry)
```

## ۵. کامیت و پوش
```
git add -A
git commit -m "port OpenVPN outbound from sing-box-extended"
git push
```

بعد از پوش، هش کامیت جدید رو بهم بده تا `get_source_env.sh` رو آپدیت کنم و بریم سراغ فعال‌سازی build tag و ادیت `ConfigBuilder.kt`.
