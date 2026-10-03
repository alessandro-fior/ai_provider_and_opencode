\# AI Providers \& OpenCode



\## Objective



This document collects the configuration, tests and procedures used to run \*\*OpenCode\*\* as an AI agent for educational Java / Spring Boot projects.



The goal is to use multiple AI providers and models, preferably with free resources or Free Tier access, avoiding dependency on a single service.



Main repository used for testing:



```text

C:\\projects\\springboot\_agent

```



\---



\# 1. Environment



\## System



```text

Windows

CMD

```



\## OpenCode



Check the version:



```cmd

opencode --version

```



Verified version:



```text

1.18.34

```



Installation path:



```cmd

where opencode

```



Verified output:



```text

C:\\Users\\Alessandro FIOR\\AppData\\Roaming\\npm\\opencode

C:\\Users\\Alessandro FIOR\\AppData\\Roaming\\npm\\opencode.cmd

```



\---



\# 2. Spring Boot Repository



Local repository:



```text

C:\\projects\\springboot\_agent

```



Main files:



```text

agent.md

readme.md

```



`agent.md` contains the agent instructions.



`readme.md` contains the project roadmap and documentation.



\## Rule



`agent.md` and `readme.md` must never contain API keys, passwords or credentials.



\---



\# 3. OpenCode Authentication



To check configured credentials:



```cmd

opencode auth list

```



OpenCode manages credentials locally.



OpenCode indicates the following credentials file:



```text

\~\\.local\\share\\opencode\\auth.json

```



The credentials file \*\*must never be published to GitHub\*\*.



Never put API keys in:



```text

agent.md

readme.md

AI\_PROVIDERS.md

.env

Git repositories

```



API keys must remain local and private.



\---



\# 4. Configured Providers



Current verified status:



| Provider | Status | Method |

|---|---|---|

| NVIDIA | ✅ Configured and working | API |

| Groq | ✅ Configured | API |

| GitHub Copilot | ✅ Configured | OAuth |

| Google / Gemini API | ⏳ Not configured directly | API |

| Cerebras | ⏳ To be verified | API |

| Direct DeepSeek API | ⏳ To be verified | API |

| OpenCode Free Tier | ⚠️ Problem encountered | Free Tier |



Current check:



```cmd

opencode auth list

```



Verified result:



```text

• Nvidia api

• GitHub Copilot oauth

• Groq api



— 3 credentials

```



\---



\# 5. NVIDIA



\## Status



```text

✅ WORKING

```



NVIDIA is currently the main provider used with OpenCode.



OpenCode has been successfully tested with NVIDIA models.



A DeepSeek model available through NVIDIA is:



```text

nvidia/deepseek-ai/deepseek-v4.1-flash

```



This makes it possible to use a DeepSeek model \*\*through NVIDIA\*\*, without necessarily configuring the direct DeepSeek provider.



\---



\# 6. Google / Gemma Models through NVIDIA



It is important to distinguish between:



```text

Google / Gemini API

```



and:



```text

Google/Gemma models available through NVIDIA

```



The command:



```cmd

opencode models | findstr /i "gemini google"

```



returned:



```text

nvidia/google/diffusiongemma-26b-a4b-it

nvidia/google/gemma-3-12b-it

nvidia/google/gemma-3-4b-it

nvidia/google/gemma-4-31b-it

nvidia/google/google-paligemma

```



Therefore OpenCode exposes Google/Gemma models through NVIDIA.



Example:



```text

nvidia/google/gemma-4-31b-it

```



This \*\*does not mean\*\* that the direct Google Gemini API has been configured.



\---



\# 7. DeepSeek



There are currently two different possibilities.



\## DeepSeek through NVIDIA



Verified model:



```text

nvidia/deepseek-ai/deepseek-v4.1-flash

```



This is currently the simplest verified way to use a DeepSeek model with OpenCode.



\## Direct DeepSeek API



Status:



```text

⏳ TO BE VERIFIED

```



A DeepSeek API key has been obtained, but the direct DeepSeek provider has not yet been verified in OpenCode.



Potential configuration:



```text

/connect

```



Search for:



```text

DeepSeek

```



Then verify:



```cmd

opencode auth list

```



\---



\# 8. Groq



\## Status



```text

✅ CONFIGURED

```



Configured using:



```text

/connect

```



Provider:



```text

Groq

```



Verify with:



```cmd

opencode auth list

```



Expected entry:



```text

• Groq api

```



\---



\# 9. GitHub Copilot



\## Status



```text

✅ CONFIGURED

```



Method:



```text

OAuth

```



Verify with:



```cmd

opencode auth list

```



Expected entry:



```text

• GitHub Copilot oauth

```



\---



\# 10. Gemini



\## Status



```text

⏳ NOT CONFIGURED AS A DIRECT GOOGLE PROVIDER

```



The search:



```cmd

opencode models | findstr /i "gemini google"

```



does not show a separate Google/Gemini provider in the current setup.



Instead, Google/Gemma models are available through NVIDIA:



```text

nvidia/google/...

```



Direct Gemini API access therefore remains a separate item to verify.



\---



\# 11. Cerebras



\## Status



```text

⏳ TO BE VERIFIED

```



Expected procedure:



```text

/connect

```



Search for:



```text

Cerebras

```



After configuration:



```cmd

opencode auth list

```



Verify that the provider is listed.



\---



\# 12. Model List



To display all available models:



```cmd

opencode models

```



Search for DeepSeek:



```cmd

opencode models | findstr /i "deepseek"

```



Search for Google / Gemma:



```cmd

opencode models | findstr /i "gemini google"

```



Search for Cerebras:



```cmd

opencode models | findstr /i "cerebras"

```



Search for NVIDIA Nemotron:



```cmd

opencode models | findstr /i "nemotron"

```



\---



\# 13. Starting OpenCode



Enter the project directory:



```cmd

cd C:\\projects\\springboot\_agent

```



Start OpenCode:



```cmd

opencode

```



Inside OpenCode:



```text

/models

```



is used to select a model.



To configure a provider:



```text

/connect

```



\---



\# 14. Initial Test



Minimal test:



```text

Hello, reply only OK.

```



Repository test:



```text

Read agent.md and readme.md.



Do not modify any files.



Summarize the Spring Boot project roadmap

and identify what should be the first educational module.

```



\---



\# 15. Spring Boot Project Test



Start OpenCode:



```cmd

cd C:\\projects\\springboot\_agent

opencode

```



First phase:



```text

Read agent.md and readme.md.



Do not modify either file.



Analyze the roadmap and propose the first

educational Spring Boot module.



Analyze first.

Do not create code yet.

```



After reviewing the analysis:



```text

Proceed with the first module.



Create the educational project,

build the project,

run the tests

and verify that the code works.



Do not modify agent.md or readme.md.

```



\---



\# 16. OpenCode Free Tier Problem



The OpenCode internal Free Tier was tested.



Command:



```cmd

opencode run -m opencode/mimo-v2.6-flash-free "Hello, reply only OK"

```



Error:



```text

Error from provider (Console):

OpenCode's free tier can only be used from within OpenCode

```



The same problem was also encountered inside the interactive OpenCode interface.



NVIDIA was therefore used for the working tests.



\---



\# 17. Multi-Provider Strategy



The goal is to compare multiple providers and models.



```text

&#x20;                        ┌── NVIDIA

&#x20;                        │

&#x20;                        ├── Groq

&#x20;                        │

OpenCode ────────────────┼── GitHub Copilot

&#x20;                        │

&#x20;                        ├── Cerebras

&#x20;                        │

&#x20;                        └── DeepSeek

```



Models can be compared according to:



\- code quality;

\- speed;

\- reasoning capability;

\- repository understanding;

\- ability to modify multiple files;

\- tool usage;

\- error handling;

\- explanation quality;

\- educational value;

\- ability to follow `agent.md`.



\---



\# 18. Educational Objective



The Spring Boot project should become a progressive learning laboratory.



```text

Java

&#x20; ↓

Spring Framework

&#x20; ↓

Spring Core

&#x20; ↓

Spring Expression Language

&#x20; ↓

Spring Boot

&#x20; ↓

REST

&#x20; ↓

Validation

&#x20; ↓

JDBC

&#x20; ↓

JPA

&#x20; ↓

Security

&#x20; ↓

Testing

&#x20; ↓

Modern Java

&#x20; ↓

Java 21+

```



Each module should contain:



```text

code

README.md

examples

tests

explanation

historical comparison

```



\---



\# 19. API Key Security Rule



Never commit API keys to Git repositories.



Before running:



```cmd

git add .

git commit

git push

```



check:



```cmd

git status

```



and verify the modified files.



Never publish:



```text

API keys

passwords

tokens

OAuth credentials

auth.json

.env files containing secrets

```



Use the authentication mechanisms supported by each provider:



```text

OpenCode authentication

environment variables

credential managers

```



\---



\# 20. Next Tests



```text

\[✓] NVIDIA

\[✓] Groq

\[✓] GitHub Copilot

\[✓] Google/Gemma models through NVIDIA

\[✓] DeepSeek model through NVIDIA



\[ ] Cerebras

\[ ] Direct DeepSeek API

\[ ] Direct Gemini API

```



Next steps:



```text

\[ ] compare models

\[ ] select the main models for Java/Spring

\[ ] create the first Spring Boot module

\[ ] build

\[ ] run tests

\[ ] document the results

```



\---



\# 21. Quick Commands



\### OpenCode version



```cmd

opencode --version

```



\### OpenCode path



```cmd

where opencode

```



\### Credentials



```cmd

opencode auth list

```



\### Models



```cmd

opencode models

```



\### Search Google / Gemma



```cmd

opencode models | findstr /i "gemini google"

```



\### Search DeepSeek



```cmd

opencode models | findstr /i "deepseek"

```



\### Search Nemotron



```cmd

opencode models | findstr /i "nemotron"

```



\### Start OpenCode



```cmd

cd C:\\projects\\springboot\_agent

opencode

```



\### Configure provider



```text

/connect

```



\### Select model



```text

/models

```



\---



\# Current Status



Last verified status:



```text

OpenCode 1.18.34



NVIDIA                ✅

Groq                  ✅

GitHub Copilot        ✅



DeepSeek via NVIDIA   ✅

Google/Gemma via NVIDIA ✅



Direct Gemini API     ⏳

Cerebras              ⏳

Direct DeepSeek API   ⏳



OpenCode Free Tier    ⚠️

```



This document should be updated whenever a provider or model is added, removed or verified.

