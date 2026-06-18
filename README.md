# Horiz Arooba

Shopify theme for [horizon-arooba.myshopify.com](https://horizon-arooba.myshopify.com). This repo contains the theme source and is set up for local development with the [Shopify CLI](https://shopify.dev/docs/api/shopify-cli).

## Prerequisites

Before you start, make sure you have:

- **[nvm](https://github.com/nvm-sh/nvm)** — Node version manager
- **[Shopify CLI](https://shopify.dev/docs/api/shopify-cli)** — theme development tooling
- **Store access** — collaborator or staff account on the Horizon Arooba Shopify store

Install Shopify CLI globally if you don't have it yet:

```bash
npm install -g @shopify/cli @shopify/theme
```

## Quick start

### 1. Clone and enter the project

```bash
git clone <repository-url>
cd horiz-arooba
```

### 2. Use the correct Node version

```bash
nvm use
```

If you don't have the required Node version installed yet:

```bash
nvm install
nvm use
```

### 3. Install Shopify CLI

```bash
npm install -g @shopify/cli @shopify/theme
```

Verify the install:

```bash
shopify version
```

### 4. Log in to Shopify

```bash
shopify auth login
```

Follow the browser prompt and select the **horizon-arooba** store when asked.

### 5. Pull the latest theme from the store

This downloads the live (or selected) theme into your local project:

```bash
shopify theme pull -e store
```

You'll be prompted to choose which theme to pull if one isn't already linked.

### 6. Start local development

```bash
shopify theme dev -e store
```

The CLI starts a local preview server and opens a URL in your browser. Changes you save to theme files are synced to a development theme on the store and hot-reloaded in the preview.

Press `Ctrl + C` to stop the dev server.

## Common commands

| Command | Description |
| --- | --- |
| `shopify theme dev -e store` | Run local dev server with live reload |
| `shopify theme pull -e store` | Download theme files from the store |
| `shopify theme push -e store` | Upload local theme files to the store |
| `shopify theme check` | Lint theme files for errors and best practices |
| `shopify theme list -e store` | List themes on the connected store |

## Pushing changes

When you're ready to upload your work:

```bash
shopify theme push -e store
```

Use `--unpublished` to push to a new unpublished theme (recommended for testing):

```bash
shopify theme push -e store --unpublished
```

Use `--live` only when you intend to publish directly to the live theme:

```bash
shopify theme push -e store --live
```

## Configuration

Store connection is defined in `shopify.theme.toml`:

```toml
[environments.store]
store = "horizon-arooba.myshopify.com"
```

All commands above use `-e store` to target this environment. You can add more environments (e.g. staging) by extending this file.

## Project structure

```
horiz-arooba/
├── assets/          # CSS, JavaScript, and static files
├── config/          # Theme settings and schema
├── layout/          # Base page layouts
├── locales/         # Translation files
├── sections/        # Reusable theme sections
├── snippets/        # Partial Liquid templates
├── templates/       # Page templates (JSON + Liquid)
├── shopify.theme.toml
└── README.md
```

## Troubleshooting

**Not logged in or wrong store**

```bash
shopify auth logout
shopify auth login
```

**Theme not syncing during dev**

- Confirm you're running `shopify theme dev -e store` from the project root.
- Check that your Shopify account has theme edit permissions on the store.

**`command not found: shopify`**

Install the CLI after switching Node versions with nvm:

```bash
nvm use
npm install -g @shopify/cli @shopify/theme
shopify version
```

**Node version issues**

- Run `nvm use` in the project root before any Shopify CLI commands.
- Ensure `.nvmrc` specifies a compatible Node version (LTS recommended).

## Resources

- [Shopify theme development docs](https://shopify.dev/docs/storefronts/themes)
- [Shopify CLI theme commands](https://shopify.dev/docs/api/shopify-cli/theme)
- [Liquid reference](https://shopify.dev/docs/api/liquid)
