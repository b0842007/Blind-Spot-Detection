盲區偵測警示系統：以大型車輛為例 (Blind Spot Detection & Warning System)

📌 專案簡介
本專案旨在解決大型車輛因「視野死角」與「內輪差」造成的交通意外。透過 Raspberry Pi 4B 作為核心運算平台，整合 USB Camera 進行即時物件辨識，並結合 VL53L1X 雷射測距感測器 進行精準距離監測。當系統偵測到行人或車輛進入危險範圍時，會透過 LED 燈號與蜂鳴器發出主動警示。

🛠️ 技術重點 
核心硬體: Raspberry Pi 4B, Raspberry Pi Camera / USB Camera, VL53L1X ToF Sensor.
開發語言: Python
電腦視覺: Tensorflow Lite / MobileNet-SSD (物件辨識).
作業系統: Ubuntu Server / Raspberry Pi OS.

系統架構
影像辨識模組:
利用 OpenCV 擷取影像影像。
部署預訓練模型辨識「行人」、「自行車」、「機車」及「汽車」。

測距補強模組:
使用 VL53L1X (Time-of-Flight) 感測器，提供不受光影影響的距離數據。

邏輯判斷與警示:
當物件辨識結果與測距數據同時符合「危險距離」門檻時，觸發中斷訊號控制 GPIO。

分級警示:
黃燈：偵測到物件進入監控區。
紅燈 + 蜂鳴器：物件距離過近，發出緊急避險警告。
