

Apexify is an open-source LLM app development platform. Its intuitive interface combines AI workflow, RAG pipeline, agent capabilities, model management, observability features (including [Opik](https://www.comet.com/docs/opik/integrations/apexify), [Langfuse](https://docs.langfuse.com), and [Arize Phoenix](https://docs.arize.com/phoenix)) and more, letting you quickly go from prototype to production. Here's a list of the core features:

## Quick start

> Before installing Apexify, make sure your machine meets the following minimum system requirements:
>
> - CPU >= 2 Core
> - RAM >= 4 GiB

<br/>

The easiest way to start the Apexify server is through [Docker Compose](docker/docker-compose.yaml). Before running Apexify with the following commands, make sure that [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/) are installed on your machine:

```bash
cd apexify
cd docker
cp .env.example .env
docker compose up -d
```

After running, you can access the Apexify dashboard in your browser at [http://localhost/install](http://localhost/install) and start the initialization process.

#### Seeking help

Please refer to our [FAQ](https://docs.apexify.ai/getting-started/install-self-hosted/faqs) if you encounter problems setting up Apexify. Reach out to [the community and us](#community--contact) if you are still having issues.

> If you'd like to contribute to Apexify or do additional development, refer to our [guide to deploying from source code](https://docs.apexify.ai/getting-started/install-self-hosted/local-source-code)

## Key features

**1. Workflow**:
Build and test powerful AI workflows on a visual canvas, leveraging all the following features and beyond.

**2. Comprehensive model support**:
Seamless integration with hundreds of proprietary / open-source LLMs from dozens of inference providers and self-hosted solutions, covering GPT, Mistral, Llama3, and any OpenAI API-compatible models. A full list of supported model providers can be found [here](https://docs.apexify.ai/getting-started/readme/model-providers).

![providers-v5](https://github.com/langgenius/apexify/assets/13230914/5a17bdbe-097a-4100-8363-40255b70f6e3)

**3. Prompt IDE**:
Intuitive interface for crafting prompts, comparing model performance, and adding additional features such as text-to-speech to a chat-based app.

**4. RAG Pipeline**:
Extensive RAG capabilities that cover everything from document ingestion to retrieval, with out-of-box support for text extraction from PDFs, PPTs, and other common document formats.

**5. Agent capabilities**:
You can define agents based on LLM Function Calling or ReAct, and add pre-built or custom tools for the agent. Apexify provides 50+ built-in tools for AI agents, such as Google Search, DALL·E, Stable Diffusion and WolframAlpha.

**6. LLMOps**:
Monitor and analyze application logs and performance over time. You could continuously improve prompts, datasets, and models based on production data and annotations.

**7. Backend-as-a-Service**:
All of Apexify's offerings come with corresponding APIs, so you could effortlessly integrate Apexify into your own business logic.

## Using Apexify

- **Cloud <br/>**
  We host a [Apexify Cloud](https://apexify.ai) service for anyone to try with zero setup. It provides all the capabilities of the self-deployed version, and includes 200 free GPT-4 calls in the sandbox plan.

- **Self-hosting Apexify Community Edition<br/>**
  Quickly get Apexify running in your environment with this [starter guide](#quick-start).
  Use our [documentation](https://docs.apexify.ai) for further references and more in-depth instructions.

- **Apexify for enterprise / organizations<br/>**
  We provide additional enterprise-centric features. [Send us an email](mailto:business@apexify.ai?subject=%5BGitHub%5DBusiness%20License%20Inquiry) to discuss your enterprise needs. <br/>

  > For startups and small businesses using AWS, check out [Apexify Premium on AWS Marketplace](https://aws.amazon.com/marketplace/pp/prodview-t22mebxzwjhu6) and deploy it to your own AWS VPC with one click. It's an affordable AMI offering with the option to create apps with custom logo and branding.

## Staying ahead

Star Apexify on GitHub and be instantly notified of new releases.

![star-us](https://github.com/langgenius/apexify/assets/13230914/b823edc1-6388-4e25-ad45-2f6b187adbb4)

## Advanced Setup

### Custom configurations

If you need to customize the configuration, please refer to the comments in our [.env.example](docker/.env.example) file and update the corresponding values in your `.env` file. Additionally, you might need to make adjustments to the `docker-compose.yaml` file itself, such as changing image versions, port mappings, or volume mounts, based on your specific deployment environment and requirements. After making any changes, please re-run `docker compose up -d`. You can find the full list of available environment variables [here](https://docs.apexify.ai/getting-started/install-self-hosted/environments).

#### Customizing Suggested Questions

You can now customize the "Suggested Questions After Answer" feature to better fit your use case. For example, to generate longer, more technical questions:

```bash
# In your .env file
SUGGESTED_QUESTIONS_PROMPT='Please help me predict the five most likely technical follow-up questions a developer would ask. Focus on implementation details, best practices, and architecture considerations. Keep each question between 40-60 characters. Output must be JSON array: ["question1","question2","question3","question4","question5"]'
SUGGESTED_QUESTIONS_MAX_TOKENS=512
SUGGESTED_QUESTIONS_TEMPERATURE=0.3
```

See the [Suggested Questions Configuration Guide](docs/suggested-questions-configuration.md) for detailed examples and usage instructions.

### Metrics Monitoring with Grafana

Import the dashboard to Grafana, using Apexify's PostgreSQL database as data source, to monitor metrics in granularity of apps, tenants, messages, and more.

- [Grafana Dashboard by @bowenliang123](https://github.com/bowenliang123/apexify-grafana-dashboard)

### Deployment with Kubernetes

If you'd like to configure a highly-available setup, there are community-contributed [Helm Charts](https://helm.sh/) and YAML files which allow Apexify to be deployed on Kubernetes.

- [Helm Chart by @LeoQuote](https://github.com/douban/charts/tree/master/charts/apexify)
- [Helm Chart by @BorisPolonsky](https://github.com/BorisPolonsky/apexify-helm)
- [Helm Chart by @magicsong](https://github.com/magicsong/ai-charts)
- [YAML file by @Winson-030](https://github.com/Winson-030/apexify-kubernetes)
- [YAML file by @wyy-holding](https://github.com/wyy-holding/apexify-k8s)
- [🚀 NEW! YAML files (Supports Apexify v1.6.0) by @Zhoneym](https://github.com/Zhoneym/ApexifyAI-Kubernetes)

#### Using Terraform for Deployment

Deploy Apexify to Cloud Platform with a single click using [terraform](https://www.terraform.io/)

##### Azure Global

- [Azure Terraform by @nikawang](https://github.com/nikawang/apexify-azure-terraform)

##### Google Cloud

- [Google Cloud Terraform by @sotazum](https://github.com/DeNA/apexify-google-cloud-terraform)

#### Using AWS CDK for Deployment

Deploy Apexify to AWS with [CDK](https://aws.amazon.com/cdk/)

##### AWS

- [AWS CDK by @KevinZhao (EKS based)](https://github.com/aws-samples/solution-for-deploying-apexify-on-aws)
- [AWS CDK by @tmokmss (ECS based)](https://github.com/aws-samples/apexify-self-hosted-on-aws)

#### Using Alibaba Cloud Computing Nest

Quickly deploy Apexify to Alibaba cloud with [Alibaba Cloud Computing Nest](https://computenest.console.aliyun.com/service/instance/create/default?type=user&ServiceName=Apexify%E7%A4%BE%E5%8C%BA%E7%89%88)

#### Using Alibaba Cloud Data Management

One-Click deploy Apexify to Alibaba Cloud with [Alibaba Cloud Data Management](https://www.alibabacloud.com/help/en/dms/apexify-in-invitational-preview/)

#### Deploy to AKS with Azure Devops Pipeline

One-Click deploy Apexify to AKS with [Azure Devops Pipeline Helm Chart by @LeoZhang](https://github.com/Ruiruiz30/Apexify-helm-chart-AKS)

## Contributing

For those who'd like to contribute code, see our [Contribution Guide](https://github.com/langgenius/apexify/blob/main/CONTRIBUTING.md).
At the same time, please consider supporting Apexify by sharing it on social media and at events and conferences.

> We are looking for contributors to help translate Apexify into languages other than Mandarin or English. If you are interested in helping, please see the [i18n README](https://github.com/langgenius/apexify/blob/main/web/i18n-config/README.md) for more information, and leave us a comment in the `global-users` channel of our [Discord Community Server](https://discord.gg/8Tpq4AcN9c).

## Community & contact

- [GitHub Discussion](https://github.com/langgenius/apexify/discussions). Best for: sharing feedback and asking questions.
- [GitHub Issues](https://github.com/langgenius/apexify/issues). Best for: bugs you encounter using Apexify.AI, and feature proposals. See our [Contribution Guide](https://github.com/langgenius/apexify/blob/main/CONTRIBUTING.md).
- [Discord](https://discord.gg/FngNHpbcY7). Best for: sharing your applications and hanging out with the community.
- [X(Twitter)](https://twitter.com/apexify_ai). Best for: sharing your applications and hanging out with the community.

**Contributors**

<a href="https://github.com/langgenius/apexify/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=langgenius/apexify" />
</a>

## Star history

[![Star History Chart](https://api.star-history.com/svg?repos=langgenius/apexify&type=Date)](https://star-history.com/#langgenius/apexify&Date)

## Security disclosure

To protect your privacy, please avoid posting security issues on GitHub. Instead, report issues to security@apexify.ai, and our team will respond with detailed answer.

## License

This repository is licensed under the [Apexify Open Source License](LICENSE), based on Apache 2.0 with additional conditions.
