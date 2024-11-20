# Linux 操作完整指南

## 目錄
- [基本概念](#基本概念)
- [檔案系統管理](#檔案系統管理)
- [使用者與權限管理](#使用者與權限管理)
- [系統管理指令](#系統管理指令)
- [進程管理](#進程管理)
- [網路管理](#網路管理)
- [系統監控](#系統監控)
- [常見問題排解](#常見問題排解)

## 基本概念

### Linux 檔案系統結構

重要目錄說明：
- `/`: 根目錄
- `/home`: 使用者家目錄
- `/etc`: 系統設定檔
- `/var`: 變動資料
- `/usr`: 應用程式
- `/bin`: 基本指令
- `/sbin`: 系統管理指令

## 檔案系統管理

### 基本檔案操作

```bash
# 列出目錄內容
ls -la

# 複製檔案
cp 來源檔案 目標位置

# 移動檔案
mv 來源檔案 目標位置

# 刪除檔案
rm 檔案名稱

# 建立目錄
mkdir 目錄名稱

# 刪除目錄
rmdir 目錄名稱
rm -rf 目錄名稱  # 強制刪除包含內容
```

## 使用者與權限管理

### 檔案權限說明

Linux檔案權限由三個部分組成：
- 擁有者權限 (user)
- 群組權限 (group)
- 其他用戶權限 (others)

每個部分都包含三種權限：
- r (4): 讀取
- w (2): 寫入
- x (1): 執行

### 權限管理指令

```bash
# 更改檔案權限
chmod 777 檔案名稱  # 所有人都有完整權限
chmod 644 檔案名稱  # 擁有者可讀寫，其他人只能讀

# 遞迴更改目錄權限
chmod -R 777 目錄名稱

# 更改檔案擁有者
chown 使用者:群組 檔案名稱

# 遞迴更改目錄擁有者
chown -R 使用者:群組 目錄名稱
```

### sudo 指令使用

```bash
# 以root權限執行指令
sudo 指令

# 切換到root使用者
sudo su -

# 編輯系統檔案
sudo vim /etc/檔案名稱
```

## 系統管理指令

### 套件管理

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install 套件名稱

# CentOS/RHEL
sudo yum update
sudo yum install 套件名稱
```

### 服務管理

```bash
# 啟動服務
sudo systemctl start 服務名稱

# 停止服務
sudo systemctl stop 服務名稱

# 重啟服務
sudo systemctl restart 服務名稱

# 查看服務狀態
sudo systemctl status 服務名稱
```

## 進程管理

```bash
# 查看進程
ps aux

# 查看系統資源使用
top

# 結束進程
kill 進程ID
killall 進程名稱
```

## 網路管理

```bash
# 查看網路介面
ifconfig
ip addr

# 測試網路連線
ping 網址

# 查看網路連線
netstat -tuln
```

## 系統監控

```bash
# 查看硬碟使用量
df -h

# 查看目錄大小
du -sh 目錄名稱

# 查看記憶體使用量
free -h

# 查看系統負載
uptime
```

## 常見問題排解

### 1. 權限問題

當遇到權限拒絕時：
1. 檢查檔案權限 `ls -l`
2. 確認當前用戶身份 `whoami`
3. 必要時使用 sudo
4. 適當調整權限 `chmod`

### 2. 磁碟空間不足

處理步驟：
1. `df -h` 檢查空間使用情況
2. `du -sh /*` 找出大檔案
3. 清理暫存檔 `/tmp`
4. 移除不需要的套件

### 3. 系統負載過高

診斷方法：
1. `top` 查看資源使用
2. `ps aux` 識別問題進程
3. `netstat` 檢查網路連線
4. 查看系統日誌

## 安全性建議

1. **權限管理**
   - 避免過度使用 777 權限
   - 正確設定檔案擁有者
   - 限制 sudo 使用範圍

2. **系統更新**
   - 定期更新系統
   - 安裝安全性修補程式
   - 移除不需要的服務

3. **監控與日誌**
   - 定期檢查系統日誌
   - 監控異常活動
   - 備份重要資料

## 進階工具建議

1. **系統管理**
   - htop: 互動式系統監控
   - iotop: 磁碟I/O監控
   - iftop: 網路流量監控

2. **安全工具**
   - fail2ban: 入侵防護
   - ufw: 防火牆設定
   - logwatch: 日誌分析

## 參考資源

- [Linux Documentation Project](https://tldp.org/)
- [Ubuntu Documentation](https://help.ubuntu.com/)
- [Red Hat Documentation](https://access.redhat.com/documentation/en-us/)