
<p align="right">
   <strong>English</strong> |
</p>

<div align="center">

# Maple Leaf Protocol
#### The Memory layer for your Virtual protocal

<img src="Maple Leaf Protocol.png" width="550px" alt="Portkey AI VIRTUAL SNAKE Demo showing LLM routing capabilities" style="margin-left:-35px">


[![Twitter](https://img.shields.io/twitter/url/https/twitter/follow/portkeyai?style=social&label=Follow%20%40PortkeyAI)](https://x.com/Maple_LeafVT)

</div>


# Introduction

Maple Leaf Protocol enhances AI assistants and agents with an intelligent memory layer, enabling personalized AI interactions. Maple Leaf Protocol remembers user preferences, adapts to individual needs, and continuously improves over time, making it ideal for customer support chatbots, AI assistants, and autonomous systems.

<!-- Start of Selection -->
<p style="display: flex;">
  <span style="font-size: 1.2em;">New Feature: Introducing Graph Memory. Check out our <a href="https://docs.Maple Leaf Protocol.ai/open-source/graph-memory" target="_blank">documentation</a>.</span>
</p>
<!-- End of Selection -->


### Core Features

- **Multi-Level Memory**: User, Session, and AI Agent memory retention
- **Adaptive Personalization**: Continuous improvement based on interactions
- **Developer-Friendly API**: Simple integration into various applications
- **Cross-Platform Consistency**: Uniform behavior across devices
- **Managed Service**: Hassle-free hosted solution

### How Maple Leaf Protocol works?

Maple Leaf Protocol leverages a hybrid database approach to manage and retrieve long-term memories for AI agents and assistants. Each memory is associated with a unique identifier, such as a user ID or agent ID, allowing Maple Leaf Protocol to organize and access memories specific to an individual or context.

When a message is added to the Maple Leaf Protocol using add()  method, the system extracts relevant facts and preferences and stores it across data stores: a vector database, a key-value database, and a graph database. This hybrid approach ensures that different types of information are stored in the most efficient manner, making subsequent searches quick and effective.

When an AI agent or LLM needs to recall memories, it uses the search() method. Maple Leaf Protocol then performs search across these data stores, retrieving relevant information from each source. This information is then passed through a scoring layer, which evaluates their importance based on relevance, importance, and recency. This ensures that only the most personalized and useful context is surfaced.

The retrieved memories can then be appended to the LLM's prompt as needed, enhancing the personalization and relevance of its responses.

### Use Cases

Maple Leaf Protocol empowers organizations and individuals to enhance:

- **AI Assistants and agents**: Seamless conversations with a touch of déjà vu
- **Personalized Learning**: Tailored content recommendations and progress tracking
- **Customer Support**: Context-aware assistance with user preference memory
- **Healthcare**: Patient history and treatment plan management
- **Virtual Companions**: Deeper user relationships through conversation memory
- **Productivity**: Streamlined workflows based on user habits and task history
- **Gaming**: Adaptive environments reflecting player choices and progress

## Get Started

The easiest way to set up Maple Leaf Protocol is through the managed [Maple Leaf Protocol Platform]. This hosted solution offers automatic updates, advanced analytics, and dedicated support. [Sign up] to get started.

If you prefer to self-host, use the open-source Maple Leaf Protocol package. Follow the [installation instructions](#install) to get started.

## Installation Instructions <a name="install"></a>

Install the Maple Leaf Protocol package via pip:

```bash
pip install Maple Leaf Protocol
```

Alternatively, you can use Maple Leaf Protocol with one click on the hosted platform [here].

### Basic Usage

Maple Leaf Protocol requires an LLM to function, with `gpt-4o` from OpenAI as the default. However, it supports a variety of LLMs; for details, refer to our [Supported LLMs documentation].

First step is to instantiate the memory:

```python
from Maple Leaf Protocol import Memory

m = Memory()
```

<details>
<summary>How to set OPENAI_API_KEY</summary>

```python
import os
os.environ["OPENAI_API_KEY"] = "sk-xxx"
```
</details>


You can perform the following task on the memory:

1. Add: Store a memory from any unstructured text
2. Update: Update memory of a given memory_id
3. Search: Fetch memories based on a query
4. Get: Return memories for a certain user/agent/session
5. History: Describe how a memory has changed over time for a specific memory ID

```python
# 1. Add: Store a memory from any unstructured text
result = m.add("I am working on improving my tennis skills. Suggest some online courses.", user_id="alice", metadata={"category": "hobbies"})

# Created memory --> 'Improving her tennis skills.' and 'Looking for online suggestions.'
```

```python
# 2. Update: update the memory
result = m.update(memory_id=<memory_id_1>, data="Likes to play tennis on weekends")

# Updated memory --> 'Likes to play tennis on weekends.' and 'Looking for online suggestions.'
```

```python
# 3. Search: search related memories
related_memories = m.search(query="What are Alice's hobbies?", user_id="alice")

# Retrieved memory --> 'Likes to play tennis on weekends'
```

```python
# 4. Get all memories
all_memories = m.get_all()
memory_id = all_memories["memories"][0] ["id"] # get a memory_id

# All memory items --> 'Likes to play tennis on weekends.' and 'Looking for online suggestions.'
```

```python
# 5. Get memory history for a particular memory_id
history = m.history(memory_id=<memory_id_1>)

# Logs corresponding to memory_id_1 --> {'prev_value': 'Working on improving tennis skills and interested in online courses for tennis.', 'new_value': 'Likes to play tennis on weekends' }
```

> [!TIP]
> If you prefer a hosted version without the need to set up infrastructure yourself, check out the [Maple Leaf Protocol Platform] to get started in minutes.


### Graph Memory
To initialize Graph Memory you'll need to set up your configuration with graph store providers.
Currently, we support Neo4j as a graph store provider. You can setup [Neo4j](https://neo4j.com/) locally or use the hosted [Neo4j AuraDB](https://neo4j.com/product/auradb/). 
Moreover, you also need to set the version to `v1.1` (*prior versions are not supported*). 
Here's how you can do it:

```python
from Maple Leaf Protocol import Memory

config = {
    "graph_store": {
        "provider": "neo4j",
        "config": {
            "url": "neo4j+s://xxx",
            "username": "neo4j",
            "password": "xxx"
        }
    },
    "version": "v1.1"
}

m = Memory.from_config(config_dict=config)

```

## Documentation

For detailed usage instructions and API reference, visit our documentation at [docs.Maple Leaf Protocol.ai]. Here, you can find more information on both the open-source version and the hosted [Maple Leaf Protocol Platform].

## Star History

![Star History Chart]
## Support

Join our community for support and discussions. If you have any questions, feel free to reach out to us using one of the following methods:

- [Follow us on Twitter](https://x.com/Maple_LeafVT)




## Anonymous Telemetry

We collect anonymous usage metrics to enhance our package's quality and user experience. This includes data like feature usage frequency and system info, but never personal details. The data helps us prioritize improvements and ensure compatibility. If you wish to opt-out, set the environment variable Maple Leaf Protocol_TELEMETRY=false. We prioritize data security and don't share this data externally.

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details.
