## MT103 vs PACS.008

| **MT103 Tag** | **Meaning** | **pacs.008 (ISO 20022 XML Element)** |
|---------------|-------------|---------------------------------------|
| `:20:` | Transaction Reference | `GrpHdr/MsgId` or `CdtTrfTxInf/PmtId/InstrId` |
| `:23B:` | Bank Operation Code | `CdtTrfTxInf/PmtTpInf/SvcLvl/Cd` |
| `:32A:` | Value Date, Currency, Amount | `CdtTrfTxInf/IntrBkSttlmDt` + `IntrBkSttlmAmt` |
| `:33B:` | Instructed Currency/Amount | `CdtTrfTxInf/InstdAmt` |
| `:36:` | Exchange Rate | `CdtTrfTxInf/XchgRate` |
| `:50A/K/F:` | Ordering Customer (Debtor) | `CdtTrfTxInf/Dbtr` + `DbtrAcct/Id` |
| `:52A/D:` | Ordering Institution (Debtor Agent) | `CdtTrfTxInf/DbtrAgt/FinInstnId` |
| `:53A/D:` | Sender’s Correspondent | `CdtTrfTxInf/InstgAgt/FinInstnId` *(usage varies)* |
| `:54A/D:` | Receiver’s Correspondent | `CdtTrfTxInf/InstdAgt/FinInstnId` or `IntrmyAgt` |
| `:56A/D:` | Intermediary Institution | `CdtTrfTxInf/IntrmyAgt1/FinInstnId` |
| `:57A/D:` | Creditor Agent (Beneficiary’s Bank) | `CdtTrfTxInf/CdtrAgt/FinInstnId` |
| `:59:` | Beneficiary Customer (Creditor) | `CdtTrfTxInf/Cdtr` + `CdtrAcct/Id` |
| `:70:` | Remittance Information | `CdtTrfTxInf/RmtInf/Ustrd` *(or `Strd`)* |
| `:71A:` | Charges (OUR/BEN/SHA) | `CdtTrfTxInf/ChrgBr` |
| `:71F:` | Sender’s Charges | `CdtTrfTxInf/ChrgsInf/Amt` |
| `:71G:` | Receiver’s Charges | `CdtTrfTxInf/ChrgsInf/Amt` *(depending on agent)* |
| `:72:` | Sender to Receiver Information | `CdtTrfTxInf/InstrForNxtAgt` / `InstrForCdtrAgt` |
| `:77B:` | Regulatory Reporting | `CdtTrfTxInf/RgltryRptg` |
