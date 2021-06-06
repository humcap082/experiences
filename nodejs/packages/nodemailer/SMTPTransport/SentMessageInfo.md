# SentMessageInfo

メッセージの送信結果オブジェクトのインタフェース

```typescript
    interface SentMessageInfo {
        /** includes the envelope object for the message */
        envelope: MimeNode.Envelope;
        /** most transports should return the final Message-Id value used with this property */
        messageId: string;
    }
```
