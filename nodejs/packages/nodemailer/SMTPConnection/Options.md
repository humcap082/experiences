# Options

SMTPの接続情報のオブジェクトのインタフェース

```typescript
    interface Options {
        /** defines if the connection should use SSL (if true) or not (if false) */
        secure?: boolean;
        /** turns off STARTTLS support if true */
        ignoreTLS?: boolean;
        /** forces the client to use STARTTLS. Returns an error if upgrading the connection is not possible or fails. */
        requireTLS?: boolean;
        /** tries to use STARTTLS and continues normally if it fails */
        opportunisticTLS?: boolean;
        /** optional hostname of the client, used for identifying to the server */
        name?: string;
        /** the local interface to bind to for network connections */
        localAddress?: string;
        /** how many milliseconds to wait for the connection to establish */
        connectionTimeout?: ms;
        /** how many milliseconds to wait for the greeting after connection is established */
        greetingTimeout?: ms;
        /** how many milliseconds of inactivity to allow */
        socketTimeout?: ms;
        /** optional bunyan compatible logger instance. If set to true then logs to console. If value is not set or is false then nothing is logged */
        logger?: shared.Logger | boolean;
        /** if set to true, then logs SMTP traffic without message content */
        transactionLog?: boolean;
        /** if set to true, then logs SMTP traffic and message content, otherwise logs only transaction events */
        debug?: boolean;
        /** defines preferred authentication method, e.g. ‘PLAIN’ */
        authMethod?: string;
        /** defines additional options to be passed to the socket constructor, e.g. {rejectUnauthorized: true} */
        tls?: tls.ConnectionOptions;
        /** initialized socket to use instead of creating a new one */
        socket?: net.Socket;
        /** connected socket to use instead of creating and connecting a new one. If secure option is true, then socket is upgraded from plaintext to ciphertext */
        connection?: net.Socket;
        customAuth?: CustomAuthenticationHandlers;
    }
```

## 属性

<details><summary>host</summary><section>

### host

the hostname or IP address to connect to (defaults to ‘localhost’)

```typescript
host?: string;
```

#### 型

- string

</section></details>

<details><summary>port</summary><section>

### port

the port to connect to (defaults to 25 or 465)

```typescript
port?: number;
```

#### 型

- number

</section></details>

<details><summary>auth</summary><section>

### auth

defines authentication data

```typescript
auth?: AuthenticationType;
```

#### 型

- [AuthenticationType](AuthenticationType.md)

</section></details>
