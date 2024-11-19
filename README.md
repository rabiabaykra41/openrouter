# openrouter,
!pip install openai 
from openai import OpenAI 
import os 
from openai import OpenAI 
from os import getenv 
 
os.environ["OPENROUTER_API_KEY"] = "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"

client = OpenAI(
  base_url="https://openrouter.ai/api/v1",
  api_key=getenv("OPENROUTER_API_KEY"),
)

completion = client.chat.completions.create(
  extra_headers={
    "HTTP-Referer": "$YOUR_SITE_URL", # Optional, for including your app on openrouter.ai rankings.
    "X-Title": "$YOUR_APP_NAME", # Optional. Shows in rankings on openrouter.ai.
  },
  model="meta-llama/llama-3.1-70b-instruct:free",
  messages=[
    {
      "role": "user",
      "content": "What is the meaning of life?"
    }
  ]
)
print(completion.choices[0].message.content)
