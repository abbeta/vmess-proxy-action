# Setup VMess Proxy GitHub Action

> **⚠️ This action is currently in the testing stage. If you encounter any issues or have suggestions, please [open an issue](../../issues).**

This action launches a v2ray VMess proxy using a given config file in your workflow, and (optionally) tests outbound IP and latency via the proxy.

## Usage

```yaml
- uses: your-org/vmess-proxy-action@v1
  with:
    config-path: "config.json"   # (optional) Path to your v2ray config file
    test: "true"                 # (optional) Use "true" for default test (https://www.google.com), or a custom test URL (e.g., "https://www.bing.com")
```

- If `test` is omitted or empty, no proxy test will be run.
- If `test: "true"`, latency to https://www.google.com will be measured.
- If `test` is a URL, latency to that URL will be measured.

## Example

```yaml
- uses: your-org/vmess-proxy-action@v1
  with:
    config-path: "my-v2ray-config.json"
    test: "https://www.bing.com"
```
