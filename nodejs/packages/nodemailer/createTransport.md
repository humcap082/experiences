# createTransport()

smtpサーバーとやりとりをするオブジェクト[`Transporter`](Transporter.md)を作成する。

```typescript
export function createTransport(
    transport?: SMTPTransport | SMTPTransport.Options | string,
    defaults?: SMTPTransport.Options,
): Transporter<SMTPTransport.SentMessageInfo>;

export function createTransport(
    transport: SMTPPool | SMTPPool.Options,
    defaults?: SMTPPool.Options
): Transporter<SMTPPool.SentMessageInfo>;

export function createTransport(
    transport: SendmailTransport | SendmailTransport.Options,
    defaults?: SendmailTransport.Options,
): Transporter<SendmailTransport.SentMessageInfo>;

export function createTransport(
    transport: StreamTransport | StreamTransport.Options,
    defaults?: StreamTransport.Options,
): Transporter<StreamTransport.SentMessageInfo>;

export function createTransport(
    transport: JSONTransport | JSONTransport.Options,
    defaults?: JSONTransport.Options,
): Transporter<JSONTransport.SentMessageInfo>;

export function createTransport(
    transport: SESTransport | SESTransport.Options,
    defaults?: SESTransport.Options,
): Transporter<SESTransport.SentMessageInfo>;

export function createTransport<T>(
    transport: Transport<T> | TransportOptions,
    defaults?: TransportOptions
): Transporter<T>;
```

## 引数

<details><summary>transport</summary><section>

### transport

SMTPの接続情報のオブジェクトもしくは接続URLもしくはプラグインインスタンスです。

#### 型

- [SMTPTransport](SMTPTransport.md)
- [SMTPTransport.Options](SMTPTransport/Options.md)
- string
- [SMTPPool](SMTPPool.md)
- [SMTPPool.Options](SMTPPool/Options.md)
- [SendmailTransport](SendmailTransport.md)
- [SendmailTransport.Options](SendmailTransport/Options.md)
- [StreamTransport](StreamTransport.md)
- [StreamTransport.Options](StreamTransport/Options.md)
- [JsonTransport](JsonTransport.md)
- [JsonTransport.Options](JsonTransport/Options.md)
- [SESTransport](SESTransport.md)
- [SESTransport.Options](SESTransport/Options.md)
- [Transport&lt;T&gt;](Transport.md)
- [TransportOptions](TransportOptions.md)

#### デフォルト

必須

</section></details>

<details><summary>defaults</summary><section>

### defaults

デフォルトの値を定義するオブジェクトです。

#### 型

- [SMTPTransport.Options](SMTPTransport/Options.md)
- [SMTPPool.Options](SMTPPool/Options.md)
- [SendmailTransport.Options](SendmailTransport/Options.md)
- [StreamTransport.Options](StreamTransport/Options.md)
- [JsonTransport.Options](JsonTransport/Options.md)
- [SESTransport.Options](SESTransport/Options.md)
- [TransportOptions](TransportOptions.md)

#### デフォルト

null

</section></details>

## 戻り値

- [Transporter](Transporter.md)&lt;T&gt;
- [Transporter](Transporter.md)&lt;[SMTPTransport.SentMessageInfo](SMTPTransport/SentMessageInfo.md)&gt;
- [Transporter](Transporter.md)&lt;[SMTPPool.SentMessageInfo](SMTPPool/SentMessageInfo.md)&gt;
- [Transporter](Transporter.md)&lt;[SendmailTransport.SentMessageInfo](SendmailTransport/SentMessageInfo.md)&gt;
- [Transporter](Transporter.md)&lt;[StreamTransport.SentMessageInfo](StreamTransport/SentMessageInfo.md)&gt;
- [Transporter](Transporter.md)&lt;[JSONTransport.SentMessageInfo](JSONTransport/SentMessageInfo.md)&gt;
- [Transporter](Transporter.md)&lt;[SESTransport.SentMessageInfo](SESTransport/SentMessageInfo.md)&gt;
