# MailOptions

メールの接続情報のオブジェクトのインタフェース

```typescript
    interface MailOptions extends Mail.Options {
        auth?: SMTPConnection.AuthenticationType;
        dsn?: SMTPConnection.DSNOptions;
    }
```
