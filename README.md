# Setup VMess Proxy GitHub Action

> **⚠️ This action is currently in the testing stage. If you encounter any issues or have suggestions, please [open an issue](../../issues).**

This action launches a v2ray VMess proxy using a given config file in your workflow, and (optionally) tests outbound IP and latency via the proxy.

## Usage

```yaml
- uses: abbeta/vmess-proxy-action@main
  with:
    config-path: "config.json"   # (optional) Path to your v2ray config file
    test: "true"                 # (optional) Use "true" for default test (https://www.google.com), or a custom test URL (e.g., "https://www.bing.com")
- name: Fetch data using proxy   # only this step uses the v2ray socks5 proxy
  env:                           # The env block contains English comments explaining the purpose of each environment variable.
    # Set up SOCKS5 proxy environment variables for this step only.
    # All HTTP and HTTPS requests in this step will be routed through the local v2ray proxy.
    http_proxy: "socks5://127.0.0.1:10808"   # (required) HTTP proxy address, points to local v2ray socks5 proxy
    https_proxy: "socks5://127.0.0.1:10808"  # (required) HTTPS proxy address, points to local v2ray socks5 proxy
    run: you script              # Replace you script with your actual script/command
```

- If `test` is omitted or empty, no proxy test will be run.
- If `test: "true"`, latency to https://www.google.com will be measured.
- If `test` is a URL, latency to that URL will be measured.




