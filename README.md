## MT103 vs pacs.008 
Aka: Single Customer Credit Transfer, FIToFICustomerCreditTransfer, Customer Payment, Payer to Payee.

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

## MT202 vs pacs.009

| **MT202 Tag** | **Meaning** | **pacs.009 Core (ISO 20022 XML Element)** |
|---------------|-------------|--------------------------------------------|
| `:20:` | Transaction Reference Number | `<FIToFICstmrCdtTrf><GrpHdr><MsgId>` or `<CdtTrfTxInf><PmtId><InstrId>` |
| `:21:` | Related Reference | `<CdtTrfTxInf><PmtId><EndToEndId>` or `<TxId>` *(usage depends on context)* |
| `:32A:` | Value Date, Currency, Amount | `<CdtTrfTxInf><IntrBkSttlmDt>` + `<IntrBkSttlmAmt Ccy="...">` |
| `:52A/D:` | Ordering Institution (Debtor Agent) | `<CdtTrfTxInf><DbtrAgt><FinInstnId><BICFI>` |
| `:53A/D:` | Sender’s Correspondent (optional) | `<CdtTrfTxInf><IntrmyAgt1><FinInstnId>` |
| `:54A/D:` | Receiver’s Correspondent (optional) | `<CdtTrfTxInf><IntrmyAgt2><FinInstnId>` |
| `:56A/D:` | Intermediary Institution (optional) | `<CdtTrfTxInf><IntrmyAgt3><FinInstnId>` |
| `:57A/D:` | Account With Institution (Creditor Agent) | `<CdtTrfTxInf><CdtrAgt><FinInstnId><BICFI>` |
| `:58A/D:` | Beneficiary Institution | `


## MT210 vs camt.050
| **MT210 Tag** | **Meaning** | **camt.050 (ISO 20022 XML Element)** |
|---------------|-------------|---------------------------------------|
| `:20:` | Transaction Reference Number | `<GrpHdr><MsgId>` *(message identifier)* or `<Ntfctn><Id>` |
| `:25:` | Account Identification (account to be credited) | `<Ntfctn><Acct><Id><IBAN>` or `<Othr><Id>` |
| `:32A:` | Value Date, Currency, Amount | `<Ntfctn><Ntry><ValDt><Dt>` + `<Amt Ccy="...">` |
| `:52A:` | Ordering Institution (originating bank) | `<Ntfctn><Ntry><NtryDtls><TxDtls><RltdPties><DbtrAgt>` |
| `:58A:` | Beneficiary Institution (account with bank) | `<Ntfctn><Ntry><NtryDtls><TxDtls><RltdPties><CdtrAgt>` |
| — | Message creation date/time (not explicit in MT210) | `<GrpHdr><CreDtTm>` |
| — | Number of transactions (not explicit in MT210) | `<GrpHdr><NbOfNtfctns>` |
| — | Statement/notification ID | `<Ntfctn><Id>` |
