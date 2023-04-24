# Auto-GPT-LLaMA-Plugin v.0.1.0
A simple plugin that enables users to use Auto-GPT with [GPT-LLaMA](https://github.com/keldenl/gpt-llama.cpp). This plugin rewires OpenAI's endpoint in Auto-GPT and points them to your own GPT-LLaMA instance.

### Plugin Installation Steps

1. **Download the plugin repository:**
   Download the repository as a zip file.
  
   ![Download Zip](https://raw.githubusercontent.com/BillSchumacher/Auto-GPT/master/plugin.png)

2. **Copy the plugin's Zip file:**
   Place the plugin's Zip file in the `plugins` folder of the Auto-GPT repository.

3. **Edit .env:** Add these new lines to your Auto-GPT's `.env` file, and edit the values to reflect your GPT-LLaMA installation:<br>
   ```dotenv
   ## GPT_LLAMA_BASE_URL - Custom url for the OpenAI API, # comment this line if you want to use OpenAI.
   GPT_LLAMA_BASE_URL=http://<gpt-llama instance ip>:<port>/v1
   
   ## EMBED_DIM - Define the embedding vector size, useful for models. OpenAI: 1536 (default), LLaMA 7B: 4096, LLaMA 13B: 5120, LLaMA 33B: 6656, LLaMA 65B: 8192 (Default: 1536)
   EMBED_DIM=5120
   ```
   Also edit `OPENAI_API_KEY` and enter your llama.cpp model absolute path in here.
   ```dotenv
   OPENAI_API_KEY=/mnt/some-folder/llama.cpp/models/vicuna/13B/ggml-vicuna-some-model.bin
   ```
   
4. **Allowlist the plugin (optional):**
   Add the plugin's class name `GPTLLaMAPlugin` to the `ALLOWLISTED_PLUGINS` in the `.env` file to avoid being prompted with a warning when loading the plugin:

   ```dotenv
   ALLOWLISTED_PLUGINS=GPTLLaMAPlugin
   ```

   If the plugin is not allowlisted, you will be warned before it's loaded.

