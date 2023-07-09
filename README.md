# Pull Request Description Generator

The Pull Request Description Generator is an innovative tool that utilizes the power of GPT-3 to automatically generate descriptive and informative pull request descriptions. With this tool, you can save time and effort by letting the AI model create well-crafted pull request descriptions, focusing on the motivation behind the changes and how they improve your project.

## Key Features

- **Efficient Workflow:** Streamline your development process by automating the creation of pull request descriptions.
- **Improved Communication:** Ensure clear and concise communication between team members by providing informative and comprehensive pull request descriptions.
- **Customizable Output:** Tailor the generated descriptions to match your project's style and requirements.
- **OpenAI Integration:** Utilize the GPT-3 language model from OpenAI to generate high-quality and contextually relevant pull request descriptions.

## How It Works

1. Input the title and changes made in the pull request.
2. The AI model analyzes the provided information and generates a descriptive pull request description.
3. Review and customize the generated description as needed.
4. Use the generated description in your pull request to enhance clarity and provide valuable context to reviewers.

## Benefits

- **Time-Saving:** No more struggling to come up with descriptive pull request descriptions from scratch. Let the AI handle it for you.
- **Consistency:** Maintain a consistent style and structure for your pull request descriptions throughout your project.
- **Enhanced Collaboration:** Facilitate better collaboration among team members by providing clear and informative pull request descriptions.
- **Focus on Value:** Spend more time on valuable development tasks instead of crafting pull request descriptions.

## Getting Started

To use the Pull Request Description Generator in your project, follow these steps:

1. Create an account on OpenAI, set up a payment method and get your [OpenAI API key].
2. Add the two keys as a [secret] in your repository's settings with the following names:
    - github_token: The GitHub token to use for the Action. <span style="color:red;">(Required)</span>
    - openai_api_key: The [OpenAI API key] to use, keep it hidden. <span style="color:red;">(Required)</span>
3. Create a workflow YAML file, e.g. ```.github/workflows/gpt-pr-description.yml``` with the following contents:

```yaml
name: GPT3 PR Description with OpenAI

on: pull_request

jobs:
  gpt-pr-description:
    runs-on: ubuntu-22.04

    steps:
      - uses: LightRingTechnology/gpt-pr-description@alpha
        with:
          github_token: ${{ secrets.API_TOKEN }}
          openai_api_key: ${{ secrets.OPENAI_API_KEY }}
```

You can specify more options as follow:

| Input             | Description                                           | Required | Default                    |
| ----------------- | ----------------------------------------------------- | -------- | -------------------------- |
| `github_token`    | The GitHub token to use for the Action                | Yes      |                            |
| `openai_api_key`  | The [OpenAI API key] to use, keep it hidden           | Yes      |                            |
| `pull_request_id` | The ID of the pull request to use                     | No       | Extracted from metadata    |
| `openai_model`    | The [OpenAI model] to use                             | No       | `gpt-3.5-turbo-16k`            |
| `max_tokens`      | The maximum number of **prompt tokens** to use        | No       | `1000`                     |
| `temperature`     | Higher values will make the model more creative (0-2) | No       | `0.6`                      |


[OpenAI API key]: https://help.openai.com/en/articles/4936850-where-do-i-find-my-secret-api-key
[OpenAI model]: https://platform.openai.com/docs/models
[secret]: https://docs.github.com/en/actions/security-guides/encrypted-secrets
