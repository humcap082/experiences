# Options

SMTPの接続情報などのオブジェクトのインタフェース

```typescript
    interface Options extends MailOptions, TransportOptions, SMTPConnection.Options {
        service?: string;
        getSocket?(options: Options, callback: (err: Error | null, socketOptions: any) => void): void; // TODO http.ClientRequest?
        url?: string;
    }
```

## 継承

- [MailOptions](MailOptions.md)
- [TransportOptions](../TransportOptions.md)
- [SMTPConnection.Options](../SMTPConnection/Options.md)
