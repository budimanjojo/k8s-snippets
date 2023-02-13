<div align="center">

### Kubernetes Snippets

</div>

## :book:&nbsp; Overview

This repository contains VSCode compatible snippets for Kubernetes manifests.
The goal is to make writing k8s manifests easier without having to configure [yaml-language-server](https://github.com/redhat-developer/yaml-language-server).
I work with k8s manifests a lot and telling `yaml-language-server` to load the correct schema based on filename is painful.

This solves a lot of problem for me:

- I can preload a schema using [inlined schema](https://github.com/redhat-developer/yaml-language-server#using-inlined-schema).
- I can load schema for each kind instead of using one big schema for all native manifests (YLS default behavior).
- I don't need to rewrite or copypasta same codes again and again.
- I can create a dummy manifest painlessly.
- It can improve code consistency.

## :wrench:&nbsp; Usage

I based this repo from [friendly-snippets](https://github.com/rafamadriz/friendly-snippets).
So, this should work with what you can use `friendly-snippets` with, e.g:

- [vim-vsnip](https://github.com/hrsh7th/vim-vsnip)
- [LuaSnip](https://github.com/hrsh7th/vim-vsnip)
- [coc-snippets](https://github.com/neoclide/coc-snippets)

This should also work with VSCode, according to their [Snippet Guide](https://code.visualstudio.com/api/language-extensions/snippet-guide).

## :inbox_tray:&nbsp; Installation

You can install this into `vim` or `neovim` using your plugin manager, e.g:

```
-- Packer
use "budimanjojo/k8s-snippets"

-- Plug
Plug 'budimanjojo/k8s-snippets'

-- If you're using coc.nvim, you can use:
CocInstall https://github.com/budimanjojo/k8s-snippets@master
```

## :question:&nbsp; FAQ

**Where is the schema url coming from?**

For native kubernetes manifests (e.g kubernetes.io/v1), the schema is from [here](https://github.com/yannh/kubernetes-json-schema) which is the default for `kubernetes` in `yaml-language-server` too.
For `Fluxcd` manifests, the schema is from [here](https://github.com/JJGadgets/flux2-schemas).
For some CRDs, I use [this GH workflow](https://github.com/budimanjojo/home-cluster/blob/main/.github/workflows/publish-kubernetes-schemas.yaml) (thanks to [Devin](https://github.com/onedr0p)) to publish schemas of CRDs deployed in my cluster which you can browse at `https://schemas.budimanjojo.com/<kind>_<apiVersion>.json`.
If you want to add more snippets here, make sure you have the schema for it too.

**Why are u not using x spaces for indentation?**

I use the 2 spaces for all `yaml` indentations, including dictionaries.
Unfortunately, I don't think there's anything I can do to please everybody.

**Why don't you merge this with friendly-snippets?**

Because not everybody like having inlined schema glued in the snippet, and `friendly-snippets`'s goal is different.
Think of it like `friendly-snippet` is a general public collection while this is for people like me that write a lot of k8s manifests and are using yaml-language-server.

**Why is the snippets provided for xxx apiVersion doesn't include xxx kind?**

I have a lot of CRDs that I never have to write manifest for (i.e resource that should be managed by the operator or helm).
For those manifests, I don't feel the need to write a snippet for.
If you have stuffs that you really need, feel free to create a Pull Request here.

## :coffee:&nbsp; Acknowledgements

Thanks to:

- [friendly-snippets](https://github.com/rafamadriz/friendly-snippets) for being the base template I'm using
