# Options

メールの構成のオブジェクトのインタフェース

```typescript
    interface Options {
        /** Message-id list (an array or space separated string) */
        references?: string | string[];
        /** Apple Watch specific HTML version of the message, same usage as with text and html */
        watchHtml?: string | Buffer | Readable | AttachmentLike;
        /** AMP4EMAIL specific HTML version of the message, same usage as with text and html. Make sure it is a full and valid AMP4EMAIL document, otherwise the displaying email client falls back to html and ignores the amp part */
        amp?: string | Buffer | Readable | AmpAttachment;
        /** iCalendar event, same usage as with text and html. Event method attribute defaults to ‘PUBLISH’ or define it yourself: {method: 'REQUEST', content: iCalString}. This value is added as an additional alternative to html or text. Only utf-8 content is allowed */
        icalEvent?: string | Buffer | Readable | IcalAttachment;
        /** An object or array of additional header fields */
        headers?: Headers;
        /** An object where key names are converted into list headers. List key help becomes List-Help header etc. */
        list?: ListHeaders;
        attachments?: Attachment[];
        /** An array of alternative text contents (in addition to text and html parts) */
        alternatives?: Attachment[];
        /** optional SMTP envelope, if auto generated envelope is not suitable */
        envelope?: Envelope | MimeNode.Envelope;
        /** optional Message-Id value, random value will be generated if not set */
        messageId?: string;
        /** optional Date value, current UTC string will be used if not set */
        date?: Date | string;
        /** optional transfer encoding for the textual parts */
        encoding?: string;
        /** if set then overwrites entire message output with this value. The value is not parsed, so you should still set address headers or the envelope value for the message to work */
        raw?: string | Buffer | Readable | AttachmentLike;
        /** set explicitly which encoding to use for text parts (quoted-printable or base64). If not set then encoding is detected from text content (mostly ascii means quoted-printable, otherwise base64) */
        textEncoding?: TextEncoding;
        /** if set to true then fails with an error when a node tries to load content from URL */
        disableUrlAccess?: boolean;
        /** if set to true then fails with an error when a node tries to load content from a file */
        disableFileAccess?: boolean;
        /** is an object with DKIM options */
        dkim?: DKIM.Options;
        /** method to normalize header keys for custom caseing */
        normalizeHeaderKey?(key: string): string;
        priority?: "high"|"normal"|"low";
    }
```

## 属性

<details><summary>from</summary><section>

### from

The e-mail address of the sender.

All e-mail addresses can be plain 'sender@server.com'

or formatted 'Sender Name <sender@server.com>'

```typescript
from?: string | Address;
```

#### 型

- string
- [Address](Address.md)

</section></details>

<details><summary>to</summary><section>

### to

Comma separated list or an array of recipients e-mail addresses

that will appear on the To: field

```typescript
to?: string | Address | Array<string | Address>;
```

#### 型

- string
- [Address](Address.md)
- [Array]()&lt;string&gt;;
- [Array]()&lt;[Address](Address.md)&gt;;

</section></details>

<details><summary>cc</summary><section>

### cc

Comma separated list or an array of recipients e-mail addresses

that will appear on the Cc: field

```typescript
cc?: string | Address | Array<string | Address>;
```

#### 型

- string
- [Address](Address.md)
- [Array]()&lt;string&gt;;
- [Array]()&lt;[Address](Address.md)&gt;;

</section></details>

<details><summary>bcc</summary><section>

### bcc

Comma separated list or an array of recipients e-mail addresses

that will appear on the Bcc: field

```typescript
bcc?: string | Address | Array<string | Address>;
```

#### 型

- string
- [Address](Address.md)
- [Array]()&lt;string&gt;;
- [Array]()&lt;[Address](Address.md)&gt;;

</section></details>

<details><summary>subject</summary><section>

### subject

The subject of the e-mail

```typescript
subject?: string;
```

#### 型

- string

</section></details>

<details><summary>text</summary><section>

### text

The plaintext version of the message

```typescript
text?: string | Buffer | Readable | AttachmentLike;
```

#### 型

- string
- [Buffer]()
- [Readable]()
- [AttachmentLike]()

</section></details>

<details><summary>html</summary><section>

### html

The HTML version of the message

```typescript
html?: string | Buffer | Readable | AttachmentLike;
```

#### 型

- string
- [Buffer]()
- [Readable]()
- [AttachmentLike]()

</section></details>

<details><summary>attachments</summary><section>

### attachments

An array of attachment objects

#### 型

- [Attachment]()&lsqb;&rsqb;

</section></details>

<details><summary>sender</summary><section>

### sender

An e-mail address that will appear on the Sender: field

```typescript
sender?: string | Address;
```

#### 型

- string
- [Address](Address.md)

</section></details>

<details><summary>replyTo</summary><section>

### replyTo

An e-mail address that will appear on the Reply-To: field

```typescript
replyTo?: string | Address;
```

#### 型

- string
- [Address](Address.md)

</section></details>

<details><summary>inReplyTo</summary><section>

### inReplayTo

The message-id this message is replying

```typescript
inReplyTo?: string | Address;
```

#### 型

- string
- [Address](Address.md)

</section></details>
