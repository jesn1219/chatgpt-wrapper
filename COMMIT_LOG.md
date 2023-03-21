### v0.6.4 - 19/03/2023

* **Sun Mar 19 2023:** add all core plugins to example config
* **Sun Mar 19 2023:** add init file to plugins dir, fixes #239
* **Sun Mar 19 2023:** add langchain dependency
* **Sun Mar 19 2023:** add doc for current core plugins
* **Sun Mar 19 2023:** add zap plugin

### v0.6.3 - 18/03/2023

* **Sat Mar 18 2023:** clean up template display/workflows
* **Sat Mar 18 2023:** extract description separate from overrides, fixes #238

### v0.6.2 - 18/03/2023

* **Sat Mar 18 2023:** /templates command improvements
* **Sat Mar 18 2023:** fix secondary invocations with browser backend, fixes #236

### v0.6.1 - 17/03/2023

#### **:fire_engine:Breaking Changes:fire_engine:**

The `--config-dir` and `--data-dir` arguments have changed how they interpret locations:

* Both now point to the root `chatgpt-wrapper` directory instead of a profile directory
* Config and data are still stored under `profiles/[profile]` subdirectories inside these directories
* Installations that use the default locations instead of providing CLI arguments for the locations are unaffected
* See the output of `chatgpt config` with no other arguments to see these updates reflected in the `File configuration` section

* **Fri Mar 17 2023:** find version in version.py
* **Fri Mar 17 2023:** doc for template front matter
* **Fri Mar 17 2023:** refactor config/data dir implementation, support non-profile specific templates/plugins dirs **BREAKING CHANGE**
* **Thu Mar 16 2023:** pretty up templates list output
* **Thu Mar 16 2023:** add descriptions to example templates
* **Thu Mar 16 2023:** better formatting of template front matter, use description key from front matter in /templates list
* **Thu Mar 16 2023:** enable debug logging for test scripts
* **Thu Mar 16 2023:** check for running event loop, use if found
* **Thu Mar 16 2023:** clarify how to use the sample config

### v0.6.0 - 16/03/2023

* **Thu Mar 16 2023:** fix crash after initial user creation on api backend
* **Wed Mar 15 2023:** Basic plugin functionality (alpha, subject to change)
* **Wed Mar 15 2023:** improvements to model handling
* **Tue Mar 14 2023:** set new backend model after user edit
* **Tue Mar 14 2023:** add set_model method to API backend, error handling/logging for API requests
* **Tue Mar 14 2023:** bump openai version requirement
* **Tue Mar 14 2023:** Minor bug fix: model option was not used in the wrapper (default option was hardcoded)
* **Tue Mar 14 2023:** added gpt4 model option
* **Tue Mar 14 2023:** move signal handling to base shell class, fixes #226
* **Tue Mar 14 2023:** repl_history file use platform agnostic temp dir, fixes #227
* **Mon Mar 13 2023:** Convert commands from underscore to dash
* **Mon Mar 13 2023:** don't start gen_title thread if title already exists
* **Mon Mar 13 2023:** only add check_same_thread for sqlite connections
* **Sun Feb 26 2023:** added flask to requirements
* **Sun Feb 26 2023:** improvement to docker (speed up in debugging and adding api port)

### v0.5.5 - 13/03/2023

* **Mon Mar 13 2023:** fix threading error with SQLite connections
* **Mon Mar 13 2023:** updates to example config
* **Sun Mar 12 2023:** add note about adding EDITOR env var in Windows
* **Sun Mar 12 2023:** try to get windows editor from env first
* **Sun Mar 12 2023:** add install notes for windows users

### v0.5.4 - 12/03/2023

* **Sun Mar 12 2023:** launch backend after check for config CLI arg
* **Sun Mar 12 2023:** fix ask/ask_stream signatures to support custom titles
* **Sun Mar 12 2023:** add prompt-engineer example
* **Sun Mar 12 2023:** add 'Backend configuration' section to config output
* **Sun Mar 12 2023:** temp workaround for issue #224
* **Sat Mar 11 2023:** allow overriding system message in template front matter
* **Sat Mar 11 2023:** add support for frontmatter in templates

### v0.5.3 - 11/03/2023

* **Sat Mar 11 2023:** add some example templates and API scripts
* **Sat Mar 11 2023:** allow passing custom title to ask/ask_stream in api backend
* **Sat Mar 11 2023:** init defaults for templates
* **Sat Mar 11 2023:** try to discover env editor on osx
* **Sat Mar 11 2023:** template_copy/template_delete commands
* **Sat Mar 11 2023:** kill special sauce for linux editor filetype, no longer needed
* **Fri Mar 10 2023:** ensure self.templates is a list
* **Fri Mar 10 2023:** add link to new video walkthrough
* **Fri Mar 10 2023:** fix markdown filetype for vim syntax highlighting

### v0.5.2 - 09/03/2023

* **Fri Mar 10 2023:** **HOTFIX** for broken templates directory location
* **Fri Mar 10 2023:** indicator for current conversation in /history list
* **Fri Mar 10 2023:** tweak /chat help
* **Fri Mar 10 2023:** set new conversation in API backend on user login
* **Fri Mar 10 2023:** add default_user_id arg to init of API backend
* **Fri Mar 10 2023:** add tests for chatgpt-api Python module
* **Fri Mar 10 2023:** output user id in users list
* **Fri Mar 10 2023:** add utility scripts for commit log and pypi release

### v0.5.1 - 09/03/2023

 - Add completions for many more commands
 - Show/set system message (initial context message for all conversations)
 - System message aliases
 - Template management system. See below for details (alpha, subject to change)
 - Set 'markdown' filetype for editor invocations (supports syntax highlighting)
 - Add built template variables, see below for details
 - Native editor module (removes vipe dependency)

### v0.5.0 - 08/03/2023

#### **:fire_engine:Breaking Changes:fire_engine:**

 - The return values for the public methods of the `ChatGPT`/`AsyncChatGPT` classes have changed, they are now tuple with the following values:
   - `success`: Boolean, True if the operation succeeded, False if the operation failed.
   - `data`: Object, the data the command generated.
   - `message`: Human-readable message about the outcome of the operation.

 - Introduced the concept of multiple 'backends' -- see below for the currently supported ones
 - Added the 'chatgpt-api' backend, communicates via the official OpenAI REST endpoint for ChatGPT
   - Basic multi-user support (admin party at CLI)
   - Data stored in a database (SQLite by default, any configurable in SQLAlchemy allowed)
   - Allows full model customiztion
   - Numerous new shell commands and enhancements

### v0.4.3 - 03/03/2023

#### **:fire_engine:Breaking Changes:fire_engine:**

 - ChatGPT/AsyncChatGPT classes have changed how they receive configuration values, be sure to investigate the new function signatues for their __init__() and create() methods.

### What is new?

 - [New configuration system](/config.sample.yaml)
 - Added '/config' command

### v0.4.2 - 01/03/2023

 - Fix broken `ChatGPT` sync class
 - Removed nest_asyncio dependency
 - Convert CLI to use `AsyncChatGPT` class
 - Initial implementation of stop generating text response

### v0.4.1 - 28/02/2023

- REVERT BREAKING CHANGE: Asyncio module requirement _removed_ from usage of ChatGPT class, it is now a sync wrapper around the async class

### v0.4.0 - 27/02/2023

#### **:fire_engine:Breaking Changes:fire_engine:**

- Command leader changed from '!' to '/'
- Asyncio module is now required to use ChatGPT class directly (refer to [Python usage](#python))

### What is new?

#### New commands

- Added '/quit' command
- Added '/delete' support for history IDs/UUIDs
- Added '/chat' command
- Added '/switch' command
- Added '/title' command
- Added limit/offset support for '/history'

#### New features

- **_Migrated to async Playwright_**
- **_Initial API in Flask_** (see [How to use the API](#flask-api))
- Added tab completion for commands
- Added '/tmp' volume for saving Playwright session
- Added CI and CodeQL workflows
- Added simple developer debug module
- Improved session refreshing (**_/session now works!_**)
- Migrated to Prompt Toolkit

[See commit log for previous updates](#commit-log)

## OLDER RELEASES

- 21/02/2023: v0.3.17
  - Added debug mode (visible browser window).
  - @thehunmonkgroup fixed chat naming.
  - @thehunmonkgroup added !delete command to remove/hide conversations.
  - @thehunmonkgroup added --model flag to select model ('default' or 'legacy-paid' or 'legacy-free').
  - @thehunmonkgroup added !editor command to open the current prompt in an editor and send the edited prompt to ChatGPT.
  - @thehunmonkgroup added !history command to show the list of the last 20 conversations.
  - @NatLee added **docker** support.
- 17/02/2023: v0.3.16
  - Ability to open **multiple sessions in parallel**.
  - Code now works with **ChatGPT Plus** subscription.
- 14/02/2023: v0.3.15 - Updated model to text-davinci-002-render-sha (turbo model).
- 14/02/2023: v0.3.11
  - Fixed many bugs with installation. Code is refactored.
  - Now able to use the python wrapper with a **proxy**.
- 18/01/2023: v0.3.8 - Commands now are run only using !. For instance to enable read mode (for copy-paste and long prompts) you need to write now `!read` instead of `read`. This is to avoid conflicts with the chatgpt prompts. Fixed timeout issue.
- 17/01/2023: v0.3.7 - Added timeout to `ask` method to prevent hanging. Fixed return to terminal breakdown. Streaming output now is activated by default.
