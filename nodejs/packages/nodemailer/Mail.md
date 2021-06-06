# Mail&lt;T&gt;

SMTPサーバーとやりとりするクラス。

```typescript
declare class Mail<T = any> extends EventEmitter {
    options: Mail.Options;
    meta: Map<string, any>;
    dkim: DKIM;
    transporter: Transport<T>;
    logger: shared.Logger;

    /** Usage: typeof transporter.MailMessage */
    MailMessage: MailMessage<T>;

    constructor(
        transporter: Transport<T>,
        options?: TransportOptions,
        defaults?: TransportOptions
    );

    /** Closes all connections in the pool. If there is a message being sent, the connection is closed later */
    close(): void;

    /** Returns true if there are free slots in the queue */
    isIdle(): boolean;

    /** Verifies SMTP configuration */
    verify(callback: (err: Error | null, success: true) => void): void;
    verify(): Promise<true>;

    use(step: string, plugin: Mail.PluginFunction<T>): this;

    getVersionString(): string;

    /** Sets up proxy handler for a Nodemailer object */
    setupProxy(proxyUrl: string): void;

    set(
        key: 'oauth2_provision_cb',
        value: (
            user: string,
            renew: boolean,
            callback: (
                err: Error | null,
                accessToken?: string,
                expires?: number
            ) => void
        ) => void
    ): Map<string, any>;
    set(
        key:
            'proxy_handler_http'
            | 'proxy_handler_https'
            | 'proxy_handler_socks'
            | 'proxy_handler_socks5'
            | 'proxy_handler_socks4'
            | 'proxy_handler_socks4a',
        value: (
            proxy: Url,
            options: TransportOptions,
            callback: (
                err: Error | null,
                socketOptions?: { connection: Socket }
            ) => void
        ) => void
    ): Map<string, any>;
    set(key: string, value: any): Map<string, any>;

    get(key: 'oauth2_provision_cb'): (
        user: string,
        renew: boolean,
        callback: (
            err: Error | null,
            accessToken: string,
            expires: number
        ) => void
    ) => void;
    get(
        key:
            'proxy_handler_http'
            | 'proxy_handler_https'
            | 'proxy_handler_socks'
            | 'proxy_handler_socks5'
            | 'proxy_handler_socks4'
            | 'proxy_handler_socks4a'
    ): (
        proxy: Url,
        options: TransportOptions,
        callback: (
            err: Error | null,
            socketOptions: { connection: Socket }
        ) => void
    ) => void;
    get(key: string): any;

    addListener(event: 'error', listener: (err: Error) => void): this;
    addListener(event: 'idle', listener: () => void): this;
    addListener(event: 'token', listener: (token: XOAuth2.Token) => void): this;

    emit(event: 'error', error: Error): boolean;
    emit(event: 'idle'): boolean;
    emit(event: 'token', token: XOAuth2.Token): boolean;

    on(event: 'error', listener: (err: Error) => void): this;
    on(event: 'idle', listener: () => void): this;
    on(event: 'token', listener: (token: XOAuth2.Token) => void): this;

    once(event: 'error', listener: (err: Error) => void): this;
    once(event: 'idle', listener: () => void): this;
    once(event: 'token', listener: (token: XOAuth2.Token) => void): this;

    prependListener(event: 'error', listener: (err: Error) => void): this;
    prependListener(event: 'idle', listener: () => void): this;
    prependListener(event: 'end', listener: (token: XOAuth2.Token) => void): this;

    prependOnceListener(event: 'error', listener: (err: Error) => void): this;
    prependOnceListener(event: 'idle', listener: () => void): this;
    prependOnceListener(event: 'end', listener: (token: XOAuth2.Token) => void): this;

    listeners(event: 'error'): Array<(err: Error) => void>;
    listeners(event: 'idle'): Array<() => void>;
    listeners(event: 'end'): Array<(token: XOAuth2.Token) => void>;
}
```

## 継承

- [EventEmitter](EventEmitter.md)

## メソッド

<details><summary>sendMail()</summary><section>

### sendMail()

Sends an email using the preselected transport object

```typescript
    sendMail(
        mailOptions: Mail.Options,
        callback: (err: Error | null, info: T) => void
    ): void;
    sendMail(mailOptions: Mail.Options): Promise<T>;
```

#### 引数

<details><summary>mailOptions</summary><section>

##### mailOptions

メールの内容

###### 型

[Mail.Options](Mail/Options.md)

</section></details>

<details><summary>callback</summary><section>

##### callback

メールの送信の結果を処理する関数。

引数のerrには実行時のエラー、infoには送信の情報が含まれる。

###### 型

(err: [Error]() &vert; null, info: T) => void

</section></details>

#### 戻り値

- void
- [Promise&lt;T&gt;]()

</section></details>