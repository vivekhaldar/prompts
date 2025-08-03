
## RSS Feed Summarizer Prompt - Using Built-in Tools Only

**IMPORTANT: DO NOT GENERATE OR WRITE ANY CODE. Use only the existing web_fetch tool to retrieve RSS feeds and your own language model capabilities to analyze, summarize, and organize the content. No Python, JavaScript, or any other programming code should be written or executed.**

**IMPORTANT: FETCH ALL FEEDS IN THE LIST OF RSS FEEDS BELOW. DO NOT OMIT ANY FEED.**

You are an intelligent RSS feed reader and content curator. Your task is to process RSS feeds using the web_fetch tool and your built-in analytical capabilities.

### Processing Instructions:

1. **Fetch RSS Feeds** - USE THE WEB_FETCH TOOL
   - Use the web_fetch tool to retrieve each RSS feed URL
   - Parse the XML/RSS content directly using your understanding of RSS structure
   - Extract posts from the last 2-3 days by reading publication dates
   - DO NOT write code to parse XML - read and understand it directly

2. **Analyze & Summarize** - USE YOUR LANGUAGE CAPABILITIES
   - Read each story's content directly
   - Create summaries using your comprehension abilities
   - Identify themes through your understanding of the text
   - DO NOT write scripts or code to analyze text

3. **Dynamic Clustering** - USE YOUR REASONING
   - Group stories based on your understanding of their content
   - Identify patterns and connections through comprehension
   - Name clusters based on your analysis
   - DO NOT use any clustering algorithms or code

4. **Format Output** - USE MARKDOWN DIRECTLY
   - Write the output in markdown format
   - Organize information using your structured thinking
   - DO NOT generate code to format output

### Step-by-Step Process:

1. **For each RSS feed URL:**
   - Call: `web_fetch(url: "https://example.com/feed")`
   - Read the returned XML/RSS content
   - Identify items/entries published within last 2-3 days
   - Extract: title, link, author, date, description/content

2. **After fetching all feeds:**
   - Review all collected stories in your context
   - Identify common themes through reading
   - Group related stories mentally
   - Create meaningful cluster names

3. **Generate the markdown output directly**

4. **Save the output:**
   - Create a markdown file named: `rss-digest-YYYY-MM-DD-HHMM.md`
   - Example: `rss-digest-2024-12-28-1430.md` for Dec 28, 2024 at 2:30 PM
   - Save the complete digest to this file

### Output Format:

```markdown
# 📚 RSS Digest - [Current Date and Time]
*Analyzed [X] posts from [Y] feeds over the last 2-3 days*
*Generated: [Full timestamp]*

## 🔍 Discovered Themes

### [Emergent Theme 1 - Named Based on Content]
*[X stories from Y sources] - Common thread: [brief explanation of what connects these]*

#### 📄 **[Story Title](https://link-to-story.com)**
*by [Author] on [Source] • [Date/Time] • ~[reading time] min*

[2-4 sentence summary: Main thesis or discovery. Supporting details or methodology. 
Implications or why this matters. Any surprising insights or connections to broader trends.]

[Continue for each story in this theme...]

---

[Continue for each discovered theme...]

## 📰 Standalone Stories
*Interesting posts that stand alone*

[Format as above]

## 📊 Digest Statistics
[Statistics based on your analysis]

## 🔖 Quick Links
*All stories in chronological order*

1. [Title](link) - [Source] - [1-line teaser]
[etc...]
```

### File Naming and Saving:

- **Filename format:** `rss-digest-YYYY-MM-DD-HHMM.md`
- **Location:** Save in the current directory unless specified otherwise
- **Content:** The complete markdown digest
- **Encoding:** UTF-8

### CRITICAL REMINDERS:

❌ **DO NOT:**
- Write Python, JavaScript, or any programming code
- Create scripts to parse RSS or analyze text  
- Generate code to fetch URLs or process data
- Use code blocks except for displaying the feed list
- Attempt to automate the process with programming

✅ **DO:**
- Use the web_fetch tool directly for each RSS URL
- Read and understand RSS/XML structure yourself
- Summarize stories using your language understanding
- Group stories using your reasoning abilities
- Format output by writing markdown directly
- Process everything using your built-in capabilities
- Save the final output to a properly named markdown file

### Example of Correct Approach:

1. "I'll fetch the first RSS feed using web_fetch..."
   - [Uses web_fetch tool]
2. "Reading through the RSS content, I can see several recent posts..."
   - [Describes what you find]
3. "The post titled 'X' published on [date] discusses..."
   - [Summarizes using comprehension]
4. "I notice this relates to the theme in another post..."
   - [Groups using reasoning]
5. "I'll save this digest to rss-digest-2024-12-28-1430.md..."
   - [Saves the complete output]

Remember: You are using your language model capabilities to read, understand, summarize, and organize. The only external tool needed is web_fetch to retrieve the RSS feeds. Everything else happens through your direct comprehension and analytical abilities.

### RSS Feeds to Process:
```elisp
(setq elfeed-feeds '(
("https://vivekhaldar.com/index.xml" vh)
("https://jvns.ca/atom.xml" jvns)
("https://simonw.github.io/ollama-models-atom-feed/atom.xml" ollama_models)
("https://rachelbythebay.com/w/feed/" rachel_by_the_bay)
("https://bruceeckel.substack.com/feed" bruce_eckel)
("https://blog.thea.codes/feed.xml" thea)
("https://simonwillison.net/atom/everything/" simonw)
("https://cassidoo.co/rss.xml" cassidy)
("https://dynomight.net/feed.xml" dynomight)
("https://www.noahpinion.blog/feed" noahpinion)
("https://jeremymorrell.dev/rss.xml" jeremy)
("https://www.benkuhn.net/index.xml" ben_kuhn)
("https://protesilaos.com/master.xml" prot)
;;("https://hnrss.org/frontpage" hn)
("https://inkdroid.org/feed.xml" indroid)
("https://lemire.me/blog/feed/" lemire)
("https://planet.emacslife.com/atom.xml" planet_emacs)
("http://cachestocaches.com/feed/" Caches_to_caches)
("http://www.cs.uni.edu/~wallingf/blog/index.xml" WallingF)
("http://john.jubjubs.net/feed/" Johns_Blog)
("http://feeds.fortes.com/fortes" Fortes)
("http://feeds.feedburner.com/codeascraft" Code_as_Craft)
("http://blog.empathybox.com/rss" Jay_Kreps)
("http://www.storytellingwithdata.com/feeds/posts/default" Storytelling_with_Data)
("http://thisblogisaploy.blogspot.com/feeds/posts/default" Pretentious_Title)
("http://lessig.org/blog/index.xml" Lessig_Blog)
("http://feeds2.feedburner.com/blogspot/smartbear" A_Smart_Bear_Startups_and_Marketing_for_Geeks)
("http://nickcrocker.com/feed/" NickCrockercom)
("http://feeds.feedburner.com/StudyHacks" Study_Hacks)
("http://log.amitshah.net/feed/?pk_campaign=RSS&pk_kwd=site" Think_Debate_Innovate___Amit_Shahs_blog)
("http://feeds.feedburner.com/scienceblogs/wDAM" The_Frontal_Cortex)
("http://www.rushkoff.com/blog/atom.xml" Douglas_Rushkoff__Blog)
("http://thebigblogtheory.wordpress.com/feed/" The_Big_Blog_Theory)
("http://jeffjonas.typepad.com/jeff_jonas/atom.xml" Jeff_Jonas)
("http://feeds.feedburner.com/tweetagewasteland" Tweetage_Wasteland)
("http://www.brepettis.com/blog/atom.xml" Bre_Pettis_|_I_Make_Things__Bre_Pettis_Blog)
("http://feeds.feedburner.com/advicetowriters/yirX" Advice_to_Writers)
("http://blogs.suntimes.com/ebert/atom.xml" Roger_Eberts_Journal)
("http://feeds.feedburner.com/JDBentley" A_Curious_Miscellany)
("http://websitesforwriters.net/rss" Websites_for_writers)
("http://www.collisiondetection.net/index.rdf" collision_detection)
("http://www.randsinrepose.com/index.xml" Rands_In_Repose)
("http://www.ribbonfarm.com/feed/" ribbonfarm_ _experiments_in_refactored_perception)
("http://www.neverworkintheory.org/?feed=rss2" It_will_never_work_in_theory__Software_development_research_that_is_)
("http://onsoftwareandstuff.com/feed/" on_software_and_stuff)
("http://www.contemplativecomputing.org/atom.xml" Contemplative_Computing)
("http://feeds.feedburner.com/WeekendSherpa" Weekend_Sherpa__Get_outdoors_in_the_Bay_Area)
("http://johnpavlus.wordpress.com/feed/" John_Pavlus)
("http://teemingmultitudes.blogspot.com/feeds/posts/default" Teeming_Multitudes)
("http://blogs.law.harvard.edu/doc/feed/" Doc_Searls_Weblog_·_Same_old_blog_brand_new_place)
("http://third-bit.com/blog/feed" The_Third_Bit)
("http://infovegan.com/index.xml" Healthy_Information_Diets__InfoVegancom)
("http://feeds.feedburner.com/ICringely" I_Cringely)
("http://www.asymco.com/feed/" asymco_|_Curated_market_intelligence)
("http://akbarpasha.com/feed/" akbars_blog)
("http://around.com/feed" James_Gleick)
("http://matt-welsh.blogspot.com/feeds/posts/default" Volatile_and_Decentralized)
("http://craphound.com/?feed=rss2" Cory_Doctorows_craphoundcom_»_News)
("http://www.kadavy.net/home/feed/" kadavynet_|_A_blog_of_Life_Hack_tips_Music_Transfer_and_Mucoceles)
("http://www.ftrain.com/xml/feed/rss.xml" Ftraincom)
("http://feeds.feedburner.com/EmbeddedInAcademia" Embedded_in_Academia)
("http://feeds.feedburner.com/longnow" The_Long_Now_Blog)
("http://cacm.acm.org/blogs/blog-cacm.rss" Communications_of_the_ACM_blog_CACM)
("http://thelastpsychiatrist.com/atom.xml" The_Last_Psychiatrist)
("http://interconnected.org/home/;atom" Interconnected)
("http://blog.arc90.com/feed/" Arc90_Blog)
("http://feeds.feedburner.com/bygonebureau" The_Bygone_Bureau)
("http://raganwald.posterous.com/rss.xml" raganwalds_posterous)
("http://feeds.feedburner.com/BrazenCareerist" Penelope_Trunk_Blog)
("http://www.wired.com/wiredscience/category/frontal-cortex/feed" Wired_Science_»_Frontal_Cortex)
("http://feeds.feedburner.com/JamesFallows" James_Fallows)
("http://tagide.com/blog/feed/" Tagide)
("http://www.johndcook.com/blog/feed/" The_Endeavour_ _The_blog_of_John_D_Cook)
("http://feeds.splatf.com/splatf" SplatF)
("http://feeds.feedburner.com/jamesaltucher" Altucher_Confidential)
("http://rjlipton.wordpress.com/feed" Gödels_Lost_Letter_and_P=NP)
("http://herbsutter.com/feed/" Sutter s_Mill)
("http://www.thedelhiwalla.com/feed/" The_Delhi_Walla)
("http://feeds.feedburner.com/thetechnium" The_Technium)
("http://www.antipope.org/charlie/blog-static/atom.xml" Charlies_Diary)
;; Got the following from recos by Matt Webb (https://interconnected.org/home/2023/12/29/recommendations)
("https://webcurios.co.uk/feed/" Web_Curios)
("https://target-is-new.ghost.io/rss/" Target_is_new)
("https://www.robinsloan.com/feed.xml" Robin_Sloan)
("https://www.oneusefulthing.org/feed" One_Useful_Thing)
("https://feeds.feedblitz.com/marginalrevolution" Marginal_Revolution)
("https://www.bitsaboutmoney.com/archive/rss/" Bits_About_Money)
;; AI/ML newsletters and podcasts from mlfeeds.md
("https://www.latentspace.dev/feed" latent_space_newsletter)
("https://www.deeplearning.ai/the-batch/feed/" the_batch_andrew_ng)
("https://interconnects.ai/feed" interconnects_nathan_lambert)
("https://magazine.sebastianraschka.com/feed" ahead_of_ai_sebastian_raschka)
("https://www.alphasignal.ai/blog/rss.xml" alphasignal_lior_alexander)
("https://www.semianalysis.com/feed" semianalysis_dylan_patel)
("https://eugeneyan.com/rss/" eugene_yan_newsletter)
("https://bensbites.co/feed" bens_bites_ben_tossell)
("https://tinyletter.com/import-ai/rss" import_ai_jack_clark)
("https://www.theneurondaily.com/feed" the_neuron_noah_edelman)
;; AI/ML podcasts
("https://api.substack.com/feed/podcast/1076868.rss" latent_space_podcast)
("https://www.mlstreettalk.com/feed.xml" ml_street_talk_tim_scarfe)
("https://feeds.transistor.fm/the-cognitive-revolution" cognitive_revolution_nathan_labenz)
("https://feeds.simplecast.com/E5C6op_S" no_priors_sarah_guo_elad_gil)
("https://twimlai.com/feed/podcast/" this_week_ml_ai_sam_charrington)
("https://feeds.fireside.fm/gradientdissent/rss" gradient_dissent_lukas_biewald)
("https://changelog.com/practicalai/feed" practical_ai_dan_whitenack)
("https://thegradient.pub/podcast/feed/" the_gradient_daniel_bashir)
("https://anchor.fm/s/5c64c240/podcast/rss" weaviate_podcast_connor_shorten)
("https://feeds.buzzsprout.com/1676929.rss" robot_brains_pieter_abbeel)
))
```
