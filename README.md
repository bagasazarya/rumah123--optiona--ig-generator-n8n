# rumah123--optionA--ig-generator-n8n

"You are an expert Social Media Specialist for Rumah123 Indonesia. 
Read the following latest property news article: 
Title: {{$instagramflow.json}}
Description: {{$readme.md}}

Task: Create a highly engaging, informative Instagram post caption for property seekers.
Requirements:
1. Hook in the first line related to current property trends or interest rates.
2. Concise 3-point breakdown of what this news means for homebuyers.
3. Call to Action encouraging users to comment or check Rumah123 KPR calculator.
4. Tone: Friendly, professional, relatable to Gen Z / Millennials.
5. Include relevant emojis and hashtags."

ARCHITECTURE & PROCESS DESCRIPTION:
1. Trigger: An n8n Schedule Trigger runs automatically every Monday at 09:00 AM.
2. Data Retrieval: An HTTP Request node fetches top Indonesian property news from an RSS feed / News API.
3. Content Generation: The news text is passed into an LLM node (OpenAI/Gemini) using the prompt above to produce the Instagram caption.
4. Output Routing: The generated post is sent via Webhook / Telegram Bot / Saved to database for human review before posting.

WHAT WENT WRONG & LESSONS LEARNED:
- Issue: Initial news scraping fetched raw HTML with noise, causing the LLM prompt to output messy context.
- Solution: Added a text-parser node in n8n to strip HTML and extract only clean body text before feeding it to the AI model.
- Future Improvements: Connect directly to Instagram Graph API for automatic publishing once approved, and add an AI image generator node (DALL-E 3 / Midjourney API) to auto-generate matching post visual templates.
