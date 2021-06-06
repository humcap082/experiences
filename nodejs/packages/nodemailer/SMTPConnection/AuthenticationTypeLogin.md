# AuthenticationTypeLogin

認証情報オブジェクトのインタフェース

```typescript
interface AuthenticationTypeLogin extends Credentials {
    /** indicates the authetication type, defaults to ‘login’, other option is ‘oauth2’ or ‘custom’ */
    type?: 'login' | 'Login' | 'LOGIN';
}
```

## 継承

- [Credentials](Credentials.md)
