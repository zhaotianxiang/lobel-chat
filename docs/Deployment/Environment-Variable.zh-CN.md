# 环境变量

LobeChat 在部署时提供了一些额外的配置项，使用环境变量进行设置

#### TOC

- [通用变量](#通用变量)
  - [`ACCESS_CODE`](#access_code)
  - [`CUSTOM_MODELS`](#custom_models)
- [OpenAI](#openai)
  - [`OPENAI_API_KEY`](#openai_api_key)
  - [`OPENAI_PROXY_URL`](#openai_proxy_url)
- [Azure OpenAI](#azure-openai)
  - [`USE_AZURE_OPENAI`](#use_azure_openai)
  - [`AZURE_API_KEY`](#azure_api_key)
  - [`AZURE_API_VERSION`](#azure_api_version)
- [插件服务](#插件服务)
  - [`PLUGINS_INDEX_URL`](#plugins_index_url)
  - [`PLUGIN_SETTINGS`](#plugin_settings)
- [角色服务](#角色服务)
  - [`AGENTS_INDEX_URL`](#agents_index_url)
- [数据统计](#数据统计)
  - [Vercel Analytics](#vercel-analytics)
  - [Posthog Analytics](#posthog-analytics)

## 通用变量

### `ACCESS_CODE`

- 类型：可选
- 描述：添加访问 LobeChat 服务的密码，你可以设置一个长密码以防被爆破
- 默认值：-
- 示例：`awCTe)re_r74` or `rtrt_ewee3@09!`

### `CUSTOM_MODELS`

- 类型：可选
- 描述：用来控制模型列表，使用 `+` 增加一个模型，使用 `-` 来隐藏一个模型，使用 `模型名=展示名` 来自定义模型的展示名，用英文逗号隔开。
- 默认值：`-`
- 示例：`+qwen-7b-chat,+glm-6b,-gpt-3.5-turbo,gpt-4-1106-preview=gpt-4-turbo`

上面示例表示增加 `qwen-7b-chat` 和 `glm-6b` 到模型列表，而从列表中删除 `gpt-3.5-turbo`，并将 `gpt-4-1106-preview` 模型名字展示为 `gpt-4-turbo`。如果你想先禁用所有模型，再启用指定模型，可以使用 `-all,+gpt-3.5-turbo`，则表示仅启用 `gpt-3.5-turbo`。

## OpenAI

### `OPENAI_API_KEY`

- 类型：必选
- 描述：这是你在 OpenAI 账户页面申请的 API 密钥，可以前往[这里][openai-api-page]查看
- 默认值：-
- 示例：`sk-xxxxxx...xxxxxx`

### `OPENAI_PROXY_URL`

- 类型：可选
- 描述：如果你手动配置了 OpenAI 接口代理，可以使用此配置项来覆盖默认的 OpenAI API 请求基础 URL
- 默认值：`https://api.openai.com`
- 示例：`https://api.chatanywhere.cn`

<br/>

## Azure OpenAI

如果你需要使用 Azure OpenAI 来提供模型服务，可以查阅 [使用 Azure OpenAI 部署](Deploy-with-Azure-OpenAI.zh-CN.md) 章节查看详细步骤，这里将列举和 Azure OpenAI 相关的环境变量。

### `USE_AZURE_OPENAI`

- 类型：可选
- 描述：设置该值为 `1` 开启 Azure OpenAI 配置
- 默认值：-
- 示例：`1`

### `AZURE_API_KEY`

- 类型：可选
- 描述：这是你在 Azure OpenAI 账户页面申请的 API 密钥
- 默认值：-
- 示例：`c55168be3874490ef0565d9779ecd5a6`

### `AZURE_API_VERSION`

- 类型：可选
- 描述：Azure 的 API 版本，遵循 YYYY-MM-DD 格式
- 默认值：`2023-08-01-preview`
- 示例：`2023-05-15`，查阅[最新版本][azure-api-verion-url]

## 插件服务

### `PLUGINS_INDEX_URL`

- 类型：可选
- 描述：LobeChat 插件市场的索引地址，如果你自行部署了插件市场的服务，可以使用该变量来覆盖默认的插件市场地址
- 默认值：`https://chat-plugins.lobehub.com`

### `PLUGIN_SETTINGS`

- 类型：可选
- 描述：用于配置插件的设置，使用 `插件名:设置字段=设置值` 的格式来配置插件的设置，多个设置字段用英文分号 `;` 隔开，多个插件设置使用英文逗号`,`隔开。
- 默认值：`-`
- 示例：`search-engine:SERPAPI_API_KEY=xxxxx,plugin-2:key1=value1;key2=value2`

上述示例表示设置 `search-engine` 插件的 `SERPAPI_API_KEY` 为 `xxxxx`，设置 `plugin-2` 的 `key1` 为 `value1`，`key2` 为 `value2`。生成的插件设置配置如下：

```json
{
  "plugin-2": {
    "key1": "value1",
    "key2": "value2"
  },
  "search-engine": {
    "SERPAPI_API_KEY": "xxxxx"
  }
}
```

## 角色服务

### `AGENTS_INDEX_URL`

- 类型：可选
- 描述：LobeChat 角色市场的索引地址，如果你自行部署了角色市场的服务，可以使用该变量来覆盖默认的插件市场地址
- 默认值：`https://chat-agents.lobehub.com`

## 数据统计

### Vercel Analytics

#### `NEXT_PUBLIC_ANALYTICS_VERCEL`

- 类型：可选
- 描述：用于配置 Vercel Analytics 的环境变量，当设为 `1` 时开启 Vercel Analytics
- 默认值： `-`
- 示例：`1`

#### `NEXT_PUBLIC_VERCEL_DEBUG`

- 类型：可选
- 描述：用于开启 Vercel Analytics 的调试模式
- 默认值： `-`
- 示例：`1`

### Posthog Analytics

#### `NEXT_PUBLIC_ANALYTICS_POSTHOG`

- 类型：可选
- 描述：用于开启 [PostHog Analytics][posthog-analytics-url] 的环境变量，设为 `1` 时开启 PostHog Analytics
- 默认值： `-`
- 示例：`1`

#### `NEXT_PUBLIC_POSTHOG_KEY`

- 类型：可选
- 描述：设置 PostHog 项目 Key
- 默认值： `-`
- 示例：`phc_xxxxxxxx`

#### `NEXT_PUBLIC_POSTHOG_HOST`

- 类型：可选
- 描述：设置 PostHog 服务的部署地址，默认为官方的 SAAS 地址
- 默认值：`https://app.posthog.com`
- 示例：`https://example.com`

#### `NEXT_PUBLIC_POSTHOG_DEBUG`

- 类型：可选
- 描述：开启 PostHog 的调试模式
- 默认值： `-`
- 示例：`1`

[azure-api-verion-url]: https://docs.microsoft.com/zh-cn/azure/developer/javascript/api-reference/es-modules/azure-sdk/ai-translation/translationconfiguration?view=azure-node-latest#api-version
[openai-api-page]: https://platform.openai.com/account/api-keys
[posthog-analytics-url]: https://posthog.com
