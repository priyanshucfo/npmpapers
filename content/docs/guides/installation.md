---
title: "Installation"
description: ""
summary: ""
date: 2025-02-01T14:17:29+05:30
lastmod: 2025-02-01T14:17:29+05:30
draft: false
weight: 1001
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---




{{< callout context="note" title="Note" icon="outline/info-circle" >}}
Since these are essential for any project, I assume you've already installed React or Vite, along with TailwindCSS and React Router DOM. If not, make sure to set them up before proceeding.


{{< tabs "create-new-site" >}}
{{< tab "npm" >}}

```bash {title="Install package..."}
npm install webcollectionui
```

{{< /tab >}}
{{< tab "pnpm" >}}

```bash {title="Install package..."}
pnpm install webcollectionui
```

{{< /tab >}}
{{< tab "Yarn" >}}

```bash {title="Install package..."}
yarn install webcollectionui
```

{{< /tab >}}
{{< /tabs >}}

{{< /callout >}}

After successfully installing the **webcollectionui** package, you are now ready to install components from this package. Simply run the command in your terminal to get started.


{{< tabs "create-new-site" >}}
{{< tab "npm" >}}

```bash {title="Execute commands for installing components..."}
npx add-components
```

{{< /tab >}}
{{< tab "pnpm" >}}

```bash {title="Execute commands for installing components..."}
pnpm add-components
```

{{< /tab >}}
{{< tab "Yarn" >}}

```bash {title="Execute commands for installing components..."}
yarn add-components
```

{{< /tab >}}
{{< /tabs >}}

`Here’s a list of available components in the webcollectionui package. Simply enter the names of the components you want to install and enhance your project effortlessly!`

**Available components to add: BasicFeature, BasicHome, BasicNavbar ...**

**prompt:** Enter the components you want to add (comma-separated, case-sensitive):: `Enter components name`



{{< callout context="danger" title="Danger" icon="outline/alert-octagon" >}}
You may encounter issues if the src folder is not present in your project, as all code is initially placed inside **/src/components**. Once installed, you can move the component files to any folder within your project as needed.

- Clear navigation
- User-configurable color theme
- [i18n support](/docs/guides/i18n/)
  {{< /callout >}}