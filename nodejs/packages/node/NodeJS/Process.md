# Process

NodeJSのプロセスを管理するクラスのインタフェース

```typescript
interface Process extends EventEmitter {
    /**
     * Can also be a tty.WriteStream, not typed due to limitations.
     */
    stdout: WriteStream & {
        fd: 1;
    };
    /**
     * Can also be a tty.WriteStream, not typed due to limitations.
     */
    stderr: WriteStream & {
        fd: 2;
    };
    stdin: ReadStream & {
        fd: 0;
    };
    openStdin(): Socket;
    argv: string[];
    argv0: string;
    execArgv: string[];
    execPath: string;
    abort(): never;
    chdir(directory: string): void;
    cwd(): string;
    debugPort: number;

    /**
     * The `process.emitWarning()` method can be used to emit custom or application specific process warnings.
     *
     * These can be listened for by adding a handler to the `'warning'` event.
     *
     * @param warning The warning to emit.
     * @param type When `warning` is a `string`, `type` is the name to use for the _type_ of warning being emitted. Default: `'Warning'`.
     * @param code A unique identifier for the warning instance being emitted.
     * @param ctor When `warning` is a `string`, `ctor` is an optional function used to limit the generated stack trace. Default: `process.emitWarning`.
     */
    emitWarning(warning: string | Error, ctor?: Function): void;
    emitWarning(warning: string | Error, type?: string, ctor?: Function): void;
    emitWarning(warning: string | Error, type?: string, code?: string, ctor?: Function): void;
    emitWarning(warning: string | Error, options?: EmitWarningOptions): void;

    exit(code?: number): never;
    exitCode?: number;
    getgid(): number;
    setgid(id: number | string): void;
    getuid(): number;
    setuid(id: number | string): void;
    geteuid(): number;
    seteuid(id: number | string): void;
    getegid(): number;
    setegid(id: number | string): void;
    getgroups(): number[];
    setgroups(groups: ReadonlyArray<string | number>): void;
    setUncaughtExceptionCaptureCallback(cb: ((err: Error) => void) | null): void;
    hasUncaughtExceptionCaptureCallback(): boolean;
    version: string;
    versions: ProcessVersions;
    config: {
        target_defaults: {
            cflags: any[];
            default_configuration: string;
            defines: string[];
            include_dirs: string[];
            libraries: string[];
        };
        variables: {
            clang: number;
            host_arch: string;
            node_install_npm: boolean;
            node_install_waf: boolean;
            node_prefix: string;
            node_shared_openssl: boolean;
            node_shared_v8: boolean;
            node_shared_zlib: boolean;
            node_use_dtrace: boolean;
            node_use_etw: boolean;
            node_use_openssl: boolean;
            target_arch: string;
            v8_no_strict_aliasing: number;
            v8_use_snapshot: boolean;
            visibility: string;
        };
    };
    kill(pid: number, signal?: string | number): true;
    pid: number;
    ppid: number;
    title: string;
    arch: string;
    platform: Platform;
    /** @deprecated since v14.0.0 - use `require.main` instead. */
    mainModule?: Module;
    memoryUsage: MemoryUsageFn;
    cpuUsage(previousValue?: CpuUsage): CpuUsage;
    nextTick(callback: Function, ...args: any[]): void;
    release: ProcessRelease;
    features: {
        inspector: boolean;
        debug: boolean;
        uv: boolean;
        ipv6: boolean;
        tls_alpn: boolean;
        tls_sni: boolean;
        tls_ocsp: boolean;
        tls: boolean;
    };
    /**
     * @deprecated since v14.0.0 - Calling process.umask() with no argument causes
     * the process-wide umask to be written twice. This introduces a race condition between threads,
     * and is a potential security vulnerability. There is no safe, cross-platform alternative API.
     */
    umask(): number;
    /**
     * Can only be set if not in worker thread.
     */
    umask(mask: string | number): number;
    uptime(): number;
    hrtime: HRTime;
    domain: Domain;

    // Worker
    send?(message: any, sendHandle?: any, options?: { swallowErrors?: boolean}, callback?: (error: Error | null) => void): boolean;
    disconnect(): void;
    connected: boolean;

    /**
     * The `process.allowedNodeEnvironmentFlags` property is a special,
     * read-only `Set` of flags allowable within the `NODE_OPTIONS`
     * environment variable.
     */
    allowedNodeEnvironmentFlags: ReadonlySet<string>;

    /**
     * Only available with `--experimental-report`
     */
    report?: ProcessReport;

    resourceUsage(): ResourceUsage;

    traceDeprecation: boolean;

    /* EventEmitter */
    addListener(event: "beforeExit", listener: BeforeExitListener): this;
    addListener(event: "disconnect", listener: DisconnectListener): this;
    addListener(event: "exit", listener: ExitListener): this;
    addListener(event: "rejectionHandled", listener: RejectionHandledListener): this;
    addListener(event: "uncaughtException", listener: UncaughtExceptionListener): this;
    addListener(event: "uncaughtExceptionMonitor", listener: UncaughtExceptionListener): this;
    addListener(event: "unhandledRejection", listener: UnhandledRejectionListener): this;
    addListener(event: "warning", listener: WarningListener): this;
    addListener(event: "message", listener: MessageListener): this;
    addListener(event: Signals, listener: SignalsListener): this;
    addListener(event: "newListener", listener: NewListenerListener): this;
    addListener(event: "removeListener", listener: RemoveListenerListener): this;
    addListener(event: "multipleResolves", listener: MultipleResolveListener): this;

    emit(event: "beforeExit", code: number): boolean;
    emit(event: "disconnect"): boolean;
    emit(event: "exit", code: number): boolean;
    emit(event: "rejectionHandled", promise: Promise<any>): boolean;
    emit(event: "uncaughtException", error: Error): boolean;
    emit(event: "uncaughtExceptionMonitor", error: Error): boolean;
    emit(event: "unhandledRejection", reason: any, promise: Promise<any>): boolean;
    emit(event: "warning", warning: Error): boolean;
    emit(event: "message", message: any, sendHandle: any): this;
    emit(event: Signals, signal: Signals): boolean;
    emit(event: "newListener", eventName: string | symbol, listener: (...args: any[]) => void): this;
    emit(event: "removeListener", eventName: string, listener: (...args: any[]) => void): this;
    emit(event: "multipleResolves", listener: MultipleResolveListener): this;

    on(event: "beforeExit", listener: BeforeExitListener): this;
    on(event: "disconnect", listener: DisconnectListener): this;
    on(event: "exit", listener: ExitListener): this;
    on(event: "rejectionHandled", listener: RejectionHandledListener): this;
    on(event: "uncaughtException", listener: UncaughtExceptionListener): this;
    on(event: "uncaughtExceptionMonitor", listener: UncaughtExceptionListener): this;
    on(event: "unhandledRejection", listener: UnhandledRejectionListener): this;
    on(event: "warning", listener: WarningListener): this;
    on(event: "message", listener: MessageListener): this;
    on(event: Signals, listener: SignalsListener): this;
    on(event: "newListener", listener: NewListenerListener): this;
    on(event: "removeListener", listener: RemoveListenerListener): this;
    on(event: "multipleResolves", listener: MultipleResolveListener): this;
    on(event: string | symbol, listener: (...args: any[]) => void): this;

    once(event: "beforeExit", listener: BeforeExitListener): this;
    once(event: "disconnect", listener: DisconnectListener): this;
    once(event: "exit", listener: ExitListener): this;
    once(event: "rejectionHandled", listener: RejectionHandledListener): this;
    once(event: "uncaughtException", listener: UncaughtExceptionListener): this;
    once(event: "uncaughtExceptionMonitor", listener: UncaughtExceptionListener): this;
    once(event: "unhandledRejection", listener: UnhandledRejectionListener): this;
    once(event: "warning", listener: WarningListener): this;
    once(event: "message", listener: MessageListener): this;
    once(event: Signals, listener: SignalsListener): this;
    once(event: "newListener", listener: NewListenerListener): this;
    once(event: "removeListener", listener: RemoveListenerListener): this;
    once(event: "multipleResolves", listener: MultipleResolveListener): this;

    prependListener(event: "beforeExit", listener: BeforeExitListener): this;
    prependListener(event: "disconnect", listener: DisconnectListener): this;
    prependListener(event: "exit", listener: ExitListener): this;
    prependListener(event: "rejectionHandled", listener: RejectionHandledListener): this;
    prependListener(event: "uncaughtException", listener: UncaughtExceptionListener): this;
    prependListener(event: "uncaughtExceptionMonitor", listener: UncaughtExceptionListener): this;
    prependListener(event: "unhandledRejection", listener: UnhandledRejectionListener): this;
    prependListener(event: "warning", listener: WarningListener): this;
    prependListener(event: "message", listener: MessageListener): this;
    prependListener(event: Signals, listener: SignalsListener): this;
    prependListener(event: "newListener", listener: NewListenerListener): this;
    prependListener(event: "removeListener", listener: RemoveListenerListener): this;
    prependListener(event: "multipleResolves", listener: MultipleResolveListener): this;

    prependOnceListener(event: "beforeExit", listener: BeforeExitListener): this;
    prependOnceListener(event: "disconnect", listener: DisconnectListener): this;
    prependOnceListener(event: "exit", listener: ExitListener): this;
    prependOnceListener(event: "rejectionHandled", listener: RejectionHandledListener): this;
    prependOnceListener(event: "uncaughtException", listener: UncaughtExceptionListener): this;
    prependOnceListener(event: "uncaughtExceptionMonitor", listener: UncaughtExceptionListener): this;
    prependOnceListener(event: "unhandledRejection", listener: UnhandledRejectionListener): this;
    prependOnceListener(event: "warning", listener: WarningListener): this;
    prependOnceListener(event: "message", listener: MessageListener): this;
    prependOnceListener(event: Signals, listener: SignalsListener): this;
    prependOnceListener(event: "newListener", listener: NewListenerListener): this;
    prependOnceListener(event: "removeListener", listener: RemoveListenerListener): this;
    prependOnceListener(event: "multipleResolves", listener: MultipleResolveListener): this;

    listeners(event: "beforeExit"): BeforeExitListener[];
    listeners(event: "disconnect"): DisconnectListener[];
    listeners(event: "exit"): ExitListener[];
    listeners(event: "rejectionHandled"): RejectionHandledListener[];
    listeners(event: "uncaughtException"): UncaughtExceptionListener[];
    listeners(event: "uncaughtExceptionMonitor"): UncaughtExceptionListener[];
    listeners(event: "unhandledRejection"): UnhandledRejectionListener[];
    listeners(event: "warning"): WarningListener[];
    listeners(event: "message"): MessageListener[];
    listeners(event: Signals): SignalsListener[];
    listeners(event: "newListener"): NewListenerListener[];
    listeners(event: "removeListener"): RemoveListenerListener[];
    listeners(event: "multipleResolves"): MultipleResolveListener[];
}
```

## 継承

- [EventEmitter](EventEmitter.md)

## 属性


<details><summary>env</summary><section>

### env

環境変数をもつオブジェクト

```typescript
env: ProcessEnv;
```

#### 型

[ProcessEnv](ProcessEnv.md)

</section></details>

