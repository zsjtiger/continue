# Using Code Llama with Continue

With Continue, you can use Code Llama as a drop-in replacement for GPT-4, either by running locally with Ollama or GGML or through Replicate.

If you haven't already installed Continue, you can do that [here](https://marketplace.visualstudio.com/items?itemName=Continue.continue). For more general information on customizing Continue, read [our customization docs](../customization.md).

## TogetherAI

1. Create an account [here](https://api.together.xyz/signup)
2. Copy your API key that appears on the welcome screen
3. Click the "play" button on Code Llama Instruct (13B) on the [Together Models list](https://docs.together.ai/docs/models-inference)
4. Update your Continue config file to look like this:

```python
from continuedev.src.continuedev.core.models import Models
from continuedev.src.continuedev.libs.llm.together import TogetherLLM

config = ContinueConfig(
    ...
    models=Models(
        default=TogetherLLM(
            api_key="<API_KEY>",
            model="togethercomputer/CodeLlama-13b-Instruct"
        )
    )
)
```

## Ollama

1. Download Ollama [here](https://ollama.ai/) (it should walk you through the rest of these steps)
2. Open a terminal and run `ollama pull codellama`\*
3. Change your Continue config file to look like this:
```python
from continuedev.src.continuedev.libs.llm.ollama import Ollama

config = ContinueConfig(
    ...
    models=Models(
        default=Ollama(model="codellama:7b")
    )
)
```

5. Reload the VS Code window for changes to take effect

\*Only the 7b model is available right now. The others will be ready later today or tomorrow.

## Replicate

1. Get your Replicate API key [here](https://replicate.ai/)
2. Change your Continue config file to look like this:

```python
from continuedev.src.continuedev.core.models import Models
from continuedev.src.continuedev.libs.llm.replicate import ReplicateLLM

config = ContinueConfig(
    ...
    models=Models(
        default=ReplicateLLM(
            model="<CODE_LLAMA_MODEL_ID>",
            api_key="<MY_REPLICATE_API_KEY>")
    )
)
```

3. Reload the VS Code window for changes to take effect