# AWS Config

- track **configuration changes** **over time** on acc resources
- auditing of changes, compliance with standards
- does **not prevent changes happening** itself
- **regional service**, but also supports **cross-region** & **account** aggregation
- can generate SNS notifications and near-realtime event via EventBridge & Lambda if the configuration deviation from the compliance (evaluated against **config rules**)

[[AWS Config/Untitled.png]]
