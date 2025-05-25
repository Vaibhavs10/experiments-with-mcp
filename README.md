# Experiments with MCP

At this point everyone and their mum's are talking about MCP, this repo is just a collection of experiments with it.

Mostly focused around parctical and applied aspects of MCP than theory/ architecture behind.

## Getting Started

The simplest way is to use a simple client/ library that allows you to get your feet wet as soon as possible.

I'm biased but some of the ways I recommend trying is:

1. `@huggingface/tiny-agents` (for TS fans)
2. `huggingface_hub[mcp]` (for python fans)

Let's get started:

Step 1: Clone this repo

```bash
git clone https://github.com/Vaibhavs10/experiments-with-mcp && cd experiments-with-mcp
```

Step 2 (TS): Try any of the examples

For example you can run the image-gen example like this:

```bash
npx @huggingface/tiny-agents run ./image-gen
```

Step 2 (Python):

```bash
uv pip install "huggingface_hub[mcp]>=0.32.0"
```

```bash
tiny-agents run ./image-gen
```
