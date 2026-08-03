# splunk-terraform-resources

TOML resource-spec package consumed by the pleme-io `*-forge` generators.

Declares the provider's resource surface as data, so a renderer emits the
Terraform/Pulumi/Crossplane form mechanically instead of each generator
re-encoding the same schema.

Part of the pleme-io code-generation pipeline:

```
sekkei -> takumi -> openapi-forge / iac-forge -> backend renderers
```

## License

MIT — see [LICENSE](./LICENSE).
