# SOMI: Self Oxygenation Monitoring Integration

## 系统方案
- 可穿戴设备实时监测脉氧SpO2
- 可穿戴设备BLE与手机通信，上传SpO2数据
- 手机APP与云端通信，上传SpO2数据
- 用户输入自身基线值（SpO2等）和基本情况（比如年龄，性别，基础病，吸烟史等）
- 实时计算（云端或者终端）实时值和基线之间的差值或AUC
- 根据计算结果，给与用户相应指导（在家观察，去医院，打急救电话等），或根据情况（向某中心机构）发送警报
### 具体功能模块
- 可穿戴脉氧设备（定制）
    - 传感器模块
    - BLE通信模块
    - 睡眠监测硬件
- 手机APP
    - 免责声明
    - BLE通信模块
    - 云端通信模块
    - 用户信息管理模块
    - 计算统计模块（如果计算放于云端，非必需）
    - 用户行为指导模块
    - 计算报警模块（如果只需要用户行为指导，非必需）
    - 问卷模块（基于云端通信模块）
    - 监测睡眠模块
- 数据管理中心（云端）
    - 数据存储模块
    - 数据处理/统计模块（如果计算放于终端，非必需）
    - 计算报警模块
        - 面向用户报警（如果计算放于终端，非必需）
        - 面向某机构中心报警
    - 问卷推送
    - 机器学习模块（多用户数据整合）
## 目前情况
- 依露已经找到了定制感应器的厂家
- 可穿戴设备实时监测脉氧SpO2有现有产品，并且有适配的APP（Maybe 提供二次开发API）

## TODO（赶上疫情之后的药监局审批绿色窗口时间）
- 确定药监局审批绿色窗口时间
- 评估SOMI成本（可以用外包公司开发）
    - **时间成本**
    - 开发成本
    - 产品生产成本
    - APP/小程序上线成本（Android, IOS）
    - 维护成本（云端，AP/小程序维护等）