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

## Using Local models w/ Llama.cpp

In the examples above we used hosted models via Hugging Face Inference Providers but in reality you can use any tool calling enabled LLM (even those running locally).

Arguably the best way to run local models is [llama.cpp](https://github.com/ggml-org/llama.cpp)

On a mac, you can install it via:

```bash
brew install llama.cpp
```

Once installed you can use any LLMs

```bash
llama-server --jinja -fa -hf unsloth/Qwen3-30B-A3B-GGUF:Q4_K_M -c 
```

Once the server is up, you can call tiny agents.

The only change you need is in the `agents.json` file

```diff
{
	"model": "unsloth/Qwen3-30B-A3B-GGUF:Q4_K_M",
+	"endpointUrl": "http://localhost:8080/v1",
-	"provider": "nebius",

	"servers": [
		{
			"type": "sse",
			"config": {
				"url": "https://evalstate-flux1-schnell.hf.space/gradio_api/mcp/sse"
			}
		}
	]
}
```

That's it, you can now run your agent directly!

```
npx @huggingface/tiny-agents run ./local-image-gen
```

and.. you can do the same thing via `huggingface_hub` MCPClient too:

```
tiny-agents run ./local-image-gen
```

That's it! go ahead, give it a shot!
