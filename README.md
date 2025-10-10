<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./static/browser-use-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="./static/browser-use.png">
    <img alt="Shows a black Browser Use Logo in light color mode and a white one in dark color mode." src="./static/browser-use.png"  width="full">
  </picture>
</p>

<h1 align="center">Enable AI to control your browser 🤖</h1>

🌐 Browser-use is the easiest way to connect your AI agents with the browser.
💡 See what others are building and share your projects in our [Discord](https://link.browser-use.com/discord)! Want Swag? Check out our [Merch store](https://browsermerch.com).
🌤️ Skip the setup - try our **<a href="https://cloud.browser-use.com">hosted version</a>** for instant browser automation! **[Try the cloud ☁︎](https://cloud.browser-use.com)**.

# Quick start
With pip (Python>=3.11):
```bash
pip install browser-use
```
For memory functionality (requires Python<3.13 due to PyTorch compatibility):  
```bash
pip install "browser-use[memory]"
```

Install the browser:
```bash
playwright install chromium --with-deps --no-shell
```

Spin up your agent:
```python
import asyncio
from dotenv import load_dotenv
load_dotenv()
from browser_use import Agent
from langchain_openai import ChatOpenAI

async def main():
    agent = Agent(
        task="Compare the price of gpt-4o and DeepSeek-V3",
        llm=ChatOpenAI(model="gpt-4o"),
    )
    await agent.run()

asyncio.run(main())
```

Add your API keys for the provider you want to use to your `.env` file.
```bash
OPENAI_API_KEY=
ANTHROPIC_API_KEY=
AZURE_OPENAI_ENDPOINT=
AZURE_OPENAI_KEY=
```

# Documentation
📕 [Documentation](https://docs.browser-use.com)

# Concepts

### LLM Support

Browser use works with all LLM models that are supported by [LangChain](https://python.langchain.com/v0.2/docs/integrations/chat/) e.g. GPT-4o, Claude-3.5-Sonnet, LLaMA 3.1 405B, DeepSeek-V3 and many more.

### Performance Comparison: GPT-4o vs. DeepSeek-V3

In tests, DeepSeek-V3 performed better than GPT-4o.

### Memory (experimental)

The agent can store information in memory which improves performance on repetitive tasks. This is especially useful when using a weaker model like GPT-4o-mini.

# Features

- Extract structured data from websites
- Fill out forms
- Use vision/captchas to solve challenges
- Chain multiple tasks on the same (or different) sites
- Screenshots of web pages
- Memory support for repetitive tasks
- And many more!

## Advanced Agent Workflows
Browser Use is designed to facilitate agent workflows with support for:
- [Custom actions](https://docs.browser-use.com/tutorials/custom-actions)
- [Memory](https://docs.browser-use.com/features/memory)
- [UI controllers](https://docs.browser-use.com/tutorials/ui-controller) to pause the agent midway and modify its behavior
- [Session storage](https://docs.browser-use.com/tutorials/session-storage) to persist the agent's session and rerun it

# Examples

For more examples see examples folder or join the [Discord](https://link.browser-use.com/discord) to see what others are building!

<details open>
  <summary>Customization</summary>

  ### Build custom actions
  You can integrate custom actions that will be available to the agent:
  ```python
  @browser_use.action(description='Ask me to read my messages')
  def custom_action():
      print('Reading messages...')
  ```
  ### Register custom action and use it
  ```python
  agent = Agent(custom_actions=[custom_action], ...)
  ```
  ### For more examples see the [docs](https://docs.browser-use.com/tutorials/custom-actions)
</details>

<details>
  <summary>Save the session</summary>

  You can save the session and its elements to be able to rerun it:  
  ```python
  from browser_use.browser.context import BrowserContext

  browser = BrowserContext()
  await browser.load_from_state()
  ```
  For more details, see the [docs](https://docs.browser-use.com/tutorials/session-storage)
</details>

# Roadmap
Our rough roadmap is:

### Generalization

- [ ] Add workflow recorder
- [ ] Let user record a workflow - which we can rerun with browser-use as a fallback
- [ ] Make rerunning of workflows work, even if pages change

### User Experience

- [ ] Create various templates for tutorial execution, job application, QA testing, social media, etc. which users can just copy & paste.
- [ ] Improve docs
- [ ] Make it faster

### Parallelization

- [ ] Human work is sequential. The real power of a browser agent comes into reality if we can parallelize similar tasks. For example, if you want to find contact information for 100 companies, this can all be done in parallel and reported back to a main agent, which processes the results and kicks off parallel subtasks again.

## Contributing
We love contributions! Feel free to open issues for bugs or feature requests. To contribute to the docs, check out the `/docs` folder.

## Local Setup
To learn more about the library, check out the [local setup 📕](https://docs.browser-use.com/development/local-setup).
`main` is the primary development branch with frequent changes. For production use, install a stable [versioned release](https://github.com/browser-use/browser-use/releases) instead.

---

## Swag

Want to show off your Browser-use swag? Check out our  Good contributors will receive swag for free 👀.

## Citation

If you use Browser Use in your research or project, please cite:

```bibtex
@software{browser_use2025,
  author = {VYaswanthKumar},
  title = {Browser Use: Enable AI to control your browser},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/VYaswanthKumar/Ai-agent}
}
```

 <p align="center"> </p>
