---
title: "Introducing telemetry-android-lib: OpenTelemetry for Android Observability"
date: 2025-07-02
categories: [Android, Observability, OpenTelemetry]
---

![Android observability gif](https://media.giphy.com/media/3o7aD2saalBwwftBIY/giphy.gif)
*When you finally see what your app is doing in production!*

---

Modern Android apps need more than just crash logs—they need real observability. That’s why I’m excited to introduce [`telemetry-android-lib`](https://github.com/meesum-Ali/telemetry-android-lib), an open source library that brings distributed tracing, metrics, and structured logging to your Android projects, all with seamless integration to the Grafana LGTM (Loki, Grafana, Tempo, Mimir) stack.

## ✨ Why telemetry-android-lib?

- **Distributed Tracing**: Track requests across your app and backend.
- **Metrics**: Collect app vitals—memory, CPU, battery, thread count, uptime.
- **Structured Logging**: Log with levels and context.
- **Crash Reporting**: Uncaught exceptions are automatically logged.
- **Easy Integration**: One-liner setup in your `Application` class.
- **Grafana Ready**: Pre-configured for the open observability stack.
- **Custom Exporters**: Plug in your own OpenTelemetry exporters.
- **Automatic Instrumentation**: Trace Activity lifecycle and network requests (OkHttp) with zero boilerplate.

## 🏁 Quick Start

Add the library to your project (see the [README](https://github.com/meesum-Ali/telemetry-android-lib#installation) for full instructions):

```kotlin
TelemetryManager.init(
    application = this,
    serviceName = "MyAndroidApp",
    serviceVersion = BuildConfig.VERSION_NAME,
    environment = if (BuildConfig.DEBUG) "debug" else "production",
    otlpEndpoint = "http://your-otel-collector:4317"
)
```

Start logging, tracing, and collecting metrics right away:

```kotlin
TelemetryManager.log(TelemetryManager.LogLevel.INFO, "App started")
TelemetryManager.span("user_login") {
    // Your login logic
}
TelemetryManager.incRequestCount()
```

## 🔬 Advanced Features

- **Custom Spans & Attributes**: Add rich context to your traces.
- **Automatic Activity & Network Instrumentation**: Just enable the flags.
- **Frame & Jank Metrics**: Pinpoint slow screens and UI hiccups.
- **OkHttp Interceptor**: Trace and measure all your HTTP calls.

## 🧪 Test with a Local LGTM Stack

Spin up a full observability stack locally using [otel-stack](https://github.com/meesum-Ali/otel-stack):

```sh
git clone https://github.com/meesum-Ali/otel-stack.git
cd otel-stack
docker-compose up -d
```

Point your `otlpEndpoint` to `http://localhost:4317` and view your traces, logs, and metrics in Grafana!

## 🤝 Open for Contributions!

Want to help make Android observability awesome?  
Check out the [contributing guidelines](https://github.com/meesum-Ali/telemetry-android-lib/blob/main/CONTRIBUTING.md) and join the project! Whether it’s code, docs, or ideas—PRs and issues are always welcome.

---

Ready to instrument your app?  
👉 [Get started on GitHub](https://github.com/meesum-Ali/telemetry-android-lib)

---

*Have questions or feedback? Open an issue or start a discussion on GitHub!*
