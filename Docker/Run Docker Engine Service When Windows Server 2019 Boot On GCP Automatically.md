## Run Docker Engine Service When Windows Server 2019 Boot On GCP Automatically

## Issue

使用 GDP 架設 Windows Server 2019，即便於**服務**設定將 Docker Engine 設定成**自動**，Docker 依然無法自動啟動，一旦系統重新開機必須手動至**服務**啟動 Docker Engine。

## Cause

尚不清楚。

## Solution

建立一個批次檔(.bat)，使用 **net start** 語法啟動 Docker Engine，以下範例增加 Log 紀錄啟動時間：

```bat
echo %DATE% %TIME% START >> c:\Logs\start_docker_engine_server.log
net start "Docker Engine"
echo %DATE% %TIME% END >> c:\Logs\start_docker_engine_server.log
```

於**工作排程器**建立新的基本工作，細節如下：

- **動作**設定為執行該批次檔。
- **觸發條件**設定為**系統啟動時**，並於**進階設定**將**延遲工作時間**設定為**1分鐘**。
- **一般**的**安全性選項**內，點選**不論使用者登入與否均執行**，並勾選**以最高權限執行**。


