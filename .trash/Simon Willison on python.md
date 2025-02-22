---
title: "Simon Willison on python"
source: "https://simonwillison.net/tags/python/"
author:
  - "[[Simon Willison]]"
published:
created: 2025-02-22
description: "1,103 items tagged ‘python’. The Python programming language."
tags:
  - "clippings"
---
[<svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 256 256" role="img" aria-labelledby="atomFeedTitle"><title>Atom feed for python</title><defs><linearGradient id="a" x1=".1" x2=".9" y1=".1" y2=".9"><stop offset="0" stop-color="#E3702D"></stop><stop offset=".1" stop-color="#EA7D31"></stop><stop offset=".4" stop-color="#F69537"></stop><stop offset=".5" stop-color="#FB9E3A"></stop><stop offset=".7" stop-color="#EA7C31"></stop><stop offset=".9" stop-color="#DE642B"></stop><stop offset="1" stop-color="#D95B29"></stop></linearGradient></defs><rect width="256" height="256" fill="#CC5D15" rx="55" ry="55"></rect><rect width="246" height="246" x="5" y="5" fill="#F49C52" rx="50" ry="50"></rect><rect width="236" height="236" x="10" y="10" fill="url(#a)" rx="47" ry="47"></rect><circle cx="68" cy="189" r="24" fill="#FFF"></circle><path fill="#FFF" d="M160 213h-34a82 82 0 0 0-82-82V97a116 116 0 0 1 116 116z"></path><path fill="#FFF" d="M184 213A140 140 0 0 0 44 73V38a175 175 0 0 1 175 175z"></path></svg>](https://simonwillison.net/tags/python.atom)

## 1,103 items tagged “python”

The [Python](https://www.python.org/) programming language.

### 2025

> \[...\] if your situation allows it, always try uv first. Then fall back on something else if that doesn’t work out.
> 
> It is the Pareto solution because it's easier than trying to figure out what you should do and you will rarely regret it. Indeed, the cost of moving to and from it is low, but the value it delivers is quite high.

— [Kevin Samuel](https://www.bitecode.dev/p/a-year-of-uv-pros-cons-and-should), Bite code!

[#](https://simonwillison.net/2025/Feb/15/kevin-samuel/) [15th February 2025](https://simonwillison.net/2025/Feb/15/), [8:10 pm](https://simonwillison.net/2025/Feb/15/kevin-samuel/) / [uv](https://simonwillison.net/tags/uv/), [astral](https://simonwillison.net/tags/astral/), [python](https://simonwillison.net/tags/python/)

**[files-to-prompt 0.5](https://github.com/simonw/files-to-prompt/releases/tag/0.5)**. My `files-to-prompt` tool ([originally built using Claude 3 Opus back in April](https://simonwillison.net/2024/Apr/8/files-to-prompt/)) had been accumulating a bunch of issues and PRs - I finally got around to spending some time with it and pushed a fresh release:

> - New `-n/--line-numbers` flag for including line numbers in the output. Thanks, [Dan Clayton](https://github.com/danclaytondev). [#38](https://github.com/simonw/files-to-prompt/pull/38)
> - Fix for utf-8 handling on Windows. Thanks, [David Jarman](https://github.com/david-jarman). [#36](https://github.com/simonw/files-to-prompt/pull/36)
> - `--ignore` patterns are now matched against directory names as well as file names, unless you pass the new `--ignore-files-only` flag. Thanks, [Nick Powell](https://github.com/nmpowell). [#30](https://github.com/simonw/files-to-prompt/pull/30)

I use this tool myself on an almost daily basis - it's fantastic for quickly answering questions about code. Recently I've been plugging it into Gemini 2.0 with its 2 million token context length, running recipes like this one:

```
git clone https://github.com/bytecodealliance/componentize-py
cd componentize-py
files-to-prompt . -c | llm -m gemini-2.0-pro-exp-02-05 \
  -s 'How does this work? Does it include a python compiler or AST trick of some sort?'
```

I ran that question against the [bytecodealliance/componentize-py](https://github.com/bytecodealliance/componentize-py) repo - which provides a tool for turning Python code into compiled WASM - and got [this really useful answer](https://gist.github.com/simonw/a9d72e7f903417fb49e1d7a531ee8f97).

Here's another example. I decided to have o3-mini review how Datasette handles concurrent SQLite connections from async Python code - so I ran this:

```
git clone https://github.com/simonw/datasette
cd datasette/datasette
files-to-prompt database.py utils/__init__.py -c | \
  llm -m o3-mini -o reasoning_effort high \
  -s 'Output in markdown a detailed analysis of how this code handles the challenge of running SQLite queries from a Python asyncio application. Explain how it works in the first section, then explore the pros and cons of this design. In a final section propose alternative mechanisms that might work better.'
```

Here's [the result](https://gist.github.com/simonw/76c8c433f4a65cf01a5c9121453683ab). It did an extremely good job of explaining how my code works - despite being fed just the Python and none of the other documentation. Then it made some solid recommendations for potential alternatives.

I added a couple of follow-up questions (using `llm -c`) which resulted in [a full working prototype](https://gist.github.com/simonw/76c8c433f4a65cf01a5c9121453683ab?permalink_comment_id=5438685#gistcomment-5438685) of an alternative threadpool mechanism, plus [some benchmarks](https://gist.github.com/simonw/76c8c433f4a65cf01a5c9121453683ab?permalink_comment_id=5438691#gistcomment-5438691).

One final example: I decided to see if there were any undocumented features in [Litestream](https://litestream.io/), so I checked out the repo and ran a prompt against just the `.go` files in that project:

```
git clone https://github.com/benbjohnson/litestream
cd litestream
files-to-prompt . -e go -c | llm -m o3-mini \
  -s 'Write extensive user documentation for this project in markdown'
```

Once again, o3-mini provided a [really impressively detailed](https://gist.github.com/simonw/cbf339032f99fee72af5fd5455bc7235) set of unofficial documentation derived purely from reading the source.

[#](https://simonwillison.net/2025/Feb/14/files-to-prompt/) [14th February 2025](https://simonwillison.net/2025/Feb/14/), [4:14 am](https://simonwillison.net/2025/Feb/14/files-to-prompt/) / [projects](https://simonwillison.net/tags/projects/), [llms](https://simonwillison.net/tags/llms/), [gemini](https://simonwillison.net/tags/gemini/), [llm](https://simonwillison.net/tags/llm/), [ai-assisted-programming](https://simonwillison.net/tags/ai-assisted-programming/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [ai](https://simonwillison.net/tags/ai/), [webassembly](https://simonwillison.net/tags/webassembly/), [python](https://simonwillison.net/tags/python/), [async](https://simonwillison.net/tags/async/), [datasette](https://simonwillison.net/tags/datasette/), [sqlite](https://simonwillison.net/tags/sqlite/), [litestream](https://simonwillison.net/tags/litestream/)

**[shot-scraper 1.6 with support for HTTP Archives](https://github.com/simonw/shot-scraper/releases/tag/1.6)**. New release of my [shot-scraper](https://shot-scraper.datasette.io/) CLI tool for taking screenshots and scraping web pages.

The big new feature is [HTTP Archive (HAR)](https://en.wikipedia.org/wiki/HAR_\(file_format\)) support. The new [shot-scraper har command](https://shot-scraper.datasette.io/en/stable/har.html) can now create an archive of a page and all of its dependents like this:

```
shot-scraper har https://datasette.io/
```

This produces a `datasette-io.har` file (currently 163KB) which is JSON representing the full set of requests used to render that page. Here's [a copy of that file](https://gist.github.com/simonw/b1fdf434e460814efdb89c95c354f794). You can visualize that [here using ericduran.github.io/chromeHAR](https://ericduran.github.io/chromeHAR/?url=https://gist.githubusercontent.com/simonw/b1fdf434e460814efdb89c95c354f794/raw/924c1eb12b940ff02cefa2cc068f23c9d3cc5895/datasette.har.json).

![The HAR viewer shows a line for each of the loaded resources, with options to view timing information](https://static.simonwillison.net/static/2025/har-viewer.jpg)

That JSON includes full copies of all of the responses, base64 encoded if they are binary files such as images.

You can add the `--zip` flag to instead get a `datasette-io.har.zip` file, containing JSON data in `har.har` but with the response bodies saved as separate files in that archive.

The `shot-scraper multi` command lets you run `shot-scraper` against multiple URLs in sequence, specified using a YAML file. That command now takes a `--har` option (or `--har-zip` or `--har-file name-of-file)`, [described in the documentation](https://shot-scraper.datasette.io/en/stable/multi.html#recording-to-an-http-archive), which will produce a HAR at the same time as taking the screenshots.

Shots are usually defined in YAML that looks like this:

```
- output: example.com.png
  url: http://www.example.com/
- output: w3c.org.png
  url: https://www.w3.org/
```

You can now omit the `output:` keys and generate a HAR file without taking any screenshots at all:

```
- url: http://www.example.com/
- url: https://www.w3.org/
```

Run like this:

```
shot-scraper multi shots.yml --har
```

Which outputs:

```
Skipping screenshot of 'https://www.example.com/'
Skipping screenshot of 'https://www.w3.org/'
Wrote to HAR file: trace.har
```

`shot-scraper` is built on top of Playwright, and the new features use the [browser.new\_context(record\_har\_path=...)](https://playwright.dev/python/docs/next/api/class-browser#browser-new-context-option-record-har-path) parameter.

[#](https://simonwillison.net/2025/Feb/13/shot-scraper/) [13th February 2025](https://simonwillison.net/2025/Feb/13/), [9:02 pm](https://simonwillison.net/2025/Feb/13/shot-scraper/) / [projects](https://simonwillison.net/tags/projects/), [shot-scraper](https://simonwillison.net/tags/shot-scraper/), [playwright](https://simonwillison.net/tags/playwright/), [python](https://simonwillison.net/tags/python/), [scraping](https://simonwillison.net/tags/scraping/)

**[python-build-standalone now has Python 3.14.0a5](https://github.com/astral-sh/python-build-standalone/releases/tag/20250212)**. Exciting news [from Charlie Marsh](https://twitter.com/charliermarsh/status/1889837406322565305):

> We just shipped the latest Python 3.14 alpha (3.14.0a5) to uv and python-build-standalone. This is the first release that includes the tail-calling interpreter.
> 
> Our initial benchmarks show a ~20-30% performance improvement across CPython.

This is an optimization that was first discussed [in faster-cpython](https://github.com/faster-cpython/ideas/issues/642) in January 2024, then landed earlier this month [by Ken Jin](https://github.com/python/cpython/issues/128563) and included in the 3.14a05 release. The [alpha release notes](https://docs.python.org/dev/whatsnew/3.14.html#whatsnew314-tail-call) say:

> A new type of interpreter based on tail calls has been added to CPython. For certain newer compilers, this interpreter provides significantly better performance. Preliminary numbers on our machines suggest anywhere from -3% to 30% faster Python code, and a geometric mean of 9-15% faster on pyperformance depending on platform and architecture. The baseline is Python 3.14 built with Clang 19 without this new interpreter.
> 
> This interpreter currently only works with Clang 19 and newer on x86-64 and AArch64 architectures. However, we expect that a future release of GCC will support this as well.

Including this in [python-build-standalone](https://github.com/astral-sh/python-build-standalone) means it's now trivial to try out via [uv](https://github.com/astral-sh/uv). I upgraded to the latest `uv` like this:

Then ran `uv python list` to see the available versions:

```
cpython-3.14.0a5+freethreaded-macos-aarch64-none    <download available>
cpython-3.14.0a5-macos-aarch64-none                 <download available>
cpython-3.13.2+freethreaded-macos-aarch64-none      <download available>
cpython-3.13.2-macos-aarch64-none                   <download available>
cpython-3.13.1-macos-aarch64-none                   /opt/homebrew/opt/python@3.13/bin/python3.13 -> ../Frameworks/Python.framework/Versions/3.13/bin/python3.13
```

I downloaded the new alpha like this:

```
uv python install cpython-3.14.0a5
```

And tried it out like so:

```
uv run --python 3.14.0a5 python
```

The Astral team have been using Ken's [bm\_pystones.py](https://gist.github.com/Fidget-Spinner/e7bf204bf605680b0fc1540fe3777acf) benchmarks script. I grabbed a copy like this:

```
wget 'https://gist.githubusercontent.com/Fidget-Spinner/e7bf204bf605680b0fc1540fe3777acf/raw/fa85c0f3464021a683245f075505860db5e8ba6b/bm_pystones.py'
```

And ran it with `uv`:

```
uv run --python 3.14.0a5 bm_pystones.py
```

Giving:

```
Pystone(1.1) time for 50000 passes = 0.0511138
This machine benchmarks at 978209 pystones/second
```

Inspired by Charlie's [example](https://twitter.com/charliermarsh/status/1889837406322565305) I decided to try the [hyperfine](https://github.com/sharkdp/hyperfine) benchmarking tool, which can run multiple commands to statistically compare their performance. I came up with this recipe:

```
brew install hyperfine
hyperfine \                            
  "uv run --python 3.14.0a5 bm_pystones.py" \
  "uv run --python 3.13 bm_pystones.py" \
  -n tail-calling \
  -n baseline \
  --warmup 10
```

![Running that command produced: Benchmark 1: tail-calling   Time (mean ± σ):      71.5 ms ±   0.9 ms    [User: 65.3 ms, System: 5.0 ms]   Range (min … max):    69.7 ms …  73.1 ms    40 runs   Benchmark 2: baseline   Time (mean ± σ):      79.7 ms ±   0.9 ms    [User: 73.9 ms, System: 4.5 ms]   Range (min … max):    78.5 ms …  82.3 ms    36 runs   Summary   tail-calling ran     1.12 ± 0.02 times faster than baseline](https://static.simonwillison.net/static/2025/hyperfine-uv.jpg)

So 3.14.0a5 scored 1.12 times faster than 3.13 on the benchmark (on my extremely overloaded M2 MacBook Pro).

[#](https://simonwillison.net/2025/Feb/13/python-3140a5/) [13th February 2025](https://simonwillison.net/2025/Feb/13/), [6:25 am](https://simonwillison.net/2025/Feb/13/python-3140a5/) / [uv](https://simonwillison.net/tags/uv/), [astral](https://simonwillison.net/tags/astral/), [benchmarks](https://simonwillison.net/tags/benchmarks/), [python](https://simonwillison.net/tags/python/)

### [URL-addressable Pyodide Python environments](https://simonwillison.net/2025/Feb/13/url-addressable-python/)

[![Visit URL-addressable Pyodide Python environments](https://static.simonwillison.net/static/2025/datasette-lite-bug.jpg)](https://simonwillison.net/2025/Feb/13/url-addressable-python/)

This evening I spotted [an obscure bug](https://github.com/simonw/datasette/issues/2466) in [Datasette](https://datasette.io/), using [Datasette Lite](https://github.com/simonw/datasette-lite). I figure it’s a good opportunity to highlight how useful it is to have a URL-addressable Python environment, powered by Pyodide and WebAssembly.

\[... [1,905 words](https://simonwillison.net/2025/Feb/13/url-addressable-python/)\]

**[Nomic Embed Text V2: An Open Source, Multilingual, Mixture-of-Experts Embedding Model](https://www.nomic.ai/blog/posts/nomic-embed-text-v2)** ([via](https://twitter.com/nomic_ai/status/1889721439948820665 "@nomic_ai")) Nomic continue to release the most interesting and powerful embedding models. Their latest is Embed Text V2, an Apache 2.0 licensed multi-lingual 1.9GB model (here it is [on Hugging Face](https://huggingface.co/nomic-ai/nomic-embed-text-v2-moe)) trained on "1.6 billion high-quality data pairs", which is the first embedding model I've seen to use a Mixture of Experts architecture:

> In our experiments, we found that alternating MoE layers with 8 experts and top-2 routing provides the optimal balance between performance and efficiency. This results in 475M total parameters in the model, but only 305M active during training and inference.

I first tried it out using `uv run` like this:

```
uv run \
  --with einops \
  --with sentence-transformers \
  --python 3.13 python
```

Then:

```
from sentence_transformers import SentenceTransformer
model = SentenceTransformer("nomic-ai/nomic-embed-text-v2-moe", trust_remote_code=True)
sentences = ["Hello!", "¡Hola!"]
embeddings = model.encode(sentences, prompt_name="passage")
print(embeddings)
```

Then I got it working on my laptop using the [llm-sentence-tranformers](https://github.com/simonw/llm-sentence-transformers) plugin like this:

```
llm install llm-sentence-transformers
llm install einops # additional necessary package
llm sentence-transformers register nomic-ai/nomic-embed-text-v2-moe --trust-remote-code

llm embed -m sentence-transformers/nomic-ai/nomic-embed-text-v2-moe -c 'string to embed'
```

This outputs a 768 item JSON array of floating point numbers to the terminal. These are [Matryoshka embeddings](https://huggingface.co/blog/matryoshka) which means you can truncate that down to just the first 256 items and get similarity calculations that still work albeit slightly less well.

To use this for RAG you'll need to conform to Nomic's custom prompt format. For documents to be searched:

```
search_document: text of document goes here
```

And for search queries:

```
search_query: term to search for
```

I [landed a new --prepend option](https://github.com/simonw/llm/issues/745) for the [llm embed-multi](https://llm.datasette.io/en/stable/embeddings/cli.html#llm-embed-multi) command to help with that, but it's not out in a full release just yet. (**Update**: it's now out in [LLM 0.22](https://simonwillison.net/2025/Feb/17/llm/).)

I also released [llm-sentence-transformers 0.3](https://github.com/simonw/llm-sentence-transformers/releases/tag/0.3) with some minor improvements to make running this model more smooth.

[#](https://simonwillison.net/2025/Feb/12/nomic-embed-text-v2/) [12th February 2025](https://simonwillison.net/2025/Feb/12/), [10:24 pm](https://simonwillison.net/2025/Feb/12/nomic-embed-text-v2/) / [embeddings](https://simonwillison.net/tags/embeddings/), [llm](https://simonwillison.net/tags/llm/), [nomic](https://simonwillison.net/tags/nomic/), [ai](https://simonwillison.net/tags/ai/), [rag](https://simonwillison.net/tags/rag/), [uv](https://simonwillison.net/tags/uv/), [python](https://simonwillison.net/tags/python/)

**[llm-sort](https://github.com/vagos/llm-sort)** ([via](https://lobste.rs/s/yxlisx/llm_sort_sort_input_lines_semantically "lobste.rs")) Delightful [LLM](https://llm.datasette.io/) plugin by Evangelos Lamprou which adds the ability to perform "semantic search" - allowing you to sort the contents of a file based on using a prompt against an LLM to determine sort order.

Best illustrated by these examples from the README:

```
llm sort --query "Which names is more suitable for a pet monkey?" names.txt

cat titles.txt | llm sort --query "Which book should I read to cook better?"
```

It works using this pairwise prompt, which is executed multiple times using Python's `sorted(documents, key=functools.cmp_to_key(compare_callback))` mechanism:

```
Given the query:
{query}

Compare the following two lines:

Line A:
{docA}

Line B:
{docB}

Which line is more relevant to the query? Please answer with "Line A" or "Line B".
```

From [the lobste.rs comments](https://lobste.rs/s/yxlisx/llm_sort_sort_input_lines_semantically#c_enduz7), Cole Kurashige:

> I'm not saying I'm prescient, but in The Before Times [I did something similar](https://github.com/cole-k/turksort) with Mechanical Turk

This made me realize that *so many* of the patterns we were using against Mechanical Turk a decade+ ago can provide hints about potential ways to apply LLMs.

[#](https://simonwillison.net/2025/Feb/11/llm-sort/) [11th February 2025](https://simonwillison.net/2025/Feb/11/), [8:50 pm](https://simonwillison.net/2025/Feb/11/llm-sort/) / [llm](https://simonwillison.net/tags/llm/), [plugins](https://simonwillison.net/tags/plugins/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [ai](https://simonwillison.net/tags/ai/), [llms](https://simonwillison.net/tags/llms/), [python](https://simonwillison.net/tags/python/), [mechanical-turk](https://simonwillison.net/tags/mechanical-turk/)

### [Using pip to install a Large Language Model that’s under 100MB](https://simonwillison.net/2025/Feb/7/pip-install-llm-smollm2/)

[![Visit Using pip to install a Large Language Model that's under 100MB](https://static.simonwillison.net/static/2025/smol-card.jpg)](https://simonwillison.net/2025/Feb/7/pip-install-llm-smollm2/)

I just released [llm-smollm2](https://github.com/simonw/llm-smollm2), a new plugin for [LLM](https://llm.datasette.io/) that bundles a quantized copy of the [SmolLM2-135M-Instruct](https://huggingface.co/HuggingFaceTB/SmolLM2-135M-Instruct) LLM inside of the Python package.

\[... [1,553 words](https://simonwillison.net/2025/Feb/7/pip-install-llm-smollm2/)\]

**[sqlite-s3vfs](https://github.com/uktrade/sqlite-s3vfs)** ([via](https://news.ycombinator.com/item?id=42965198#42966961 "Hacker News comment")) Neat open source project on the GitHub organisation for the UK government's Department for Business and Trade: a "Python virtual filesystem for SQLite to read from and write to S3."

I tried out [their usage example](https://github.com/uktrade/sqlite-s3vfs/blob/main/README.md#usage) by running it in a Python REPL with all of the dependencies

```
uv run --python 3.13 --with apsw --with sqlite-s3vfs --with boto3 python
```

It worked as advertised. When I listed my S3 bucket I found it had created two files - one called `demo.sqlite/0000000000` and another called `demo.sqlite/0000000001`, both 4096 bytes because each one represented a SQLite page.

The implementation is just [200 lines of Python](https://github.com/uktrade/sqlite-s3vfs/blob/main/sqlite_s3vfs.py), implementing a new SQLite Virtual Filesystem on top of [apsw.VFS](https://rogerbinns.github.io/apsw/vfs.html#vfs-class).

The README includes this warning:

> No locking is performed, so client code *must* ensure that writes do not overlap with other writes or reads. If multiple writes happen at the same time, the database will probably become corrupt and data be lost.

I wonder if the [conditional writes](https://simonwillison.net/2024/Nov/26/s3-conditional-writes/) feature added to S3 back in November could be used to protect against that happening. Tricky as there are multiple files involved, but maybe it (or a [trick like this one](https://simonwillison.net/2024/Aug/30/leader-election-with-s3-conditional-writes/)) could be used to implement some kind of exclusive lock between multiple processes?

[#](https://simonwillison.net/2025/Feb/7/sqlite-s3vfs/) [7th February 2025](https://simonwillison.net/2025/Feb/7/), [2:22 am](https://simonwillison.net/2025/Feb/7/sqlite-s3vfs/) / [apsw](https://simonwillison.net/tags/apsw/), [sqlite](https://simonwillison.net/tags/sqlite/), [python](https://simonwillison.net/tags/python/), [uv](https://simonwillison.net/tags/uv/), [s3](https://simonwillison.net/tags/s3/)

**[APSW SQLite query explainer](https://tools.simonwillison.net/apsw-query)**. Today I found out about [APSW](https://rogerbinns.github.io/apsw/)'s (Another Python SQLite Wrapper, in constant development since 2004) [apsw.ext.query\_info()](https://rogerbinns.github.io/apsw/ext.html#apsw.ext.query_info) function, which takes a SQL query and returns a *very* detailed set of information about that query - all without executing it.

It actually solves a bunch of problems I've wanted to address in Datasette - like taking an arbitrary query and figuring out how many parameters (`?`) it takes and which tables and columns are represented in the result.

I tried it out in my console (`uv run --with apsw python`) and it seemed to work really well. Then I remembered that the Pyodide project includes WebAssembly builds of a number of Python C extensions and was delighted to [find apsw on that list](https://pyodide.org/en/stable/usage/packages-in-pyodide.html).

... so I [got Claude](https://gist.github.com/simonw/8d79d2a4e746f7c8966d2ae1fea90cb3) to build me [a web interface](https://tools.simonwillison.net/apsw-query) for trying out the function, using Pyodide to run a user's query in Python in their browser via WebAssembly.

Claude didn't quite get it in one shot - I had to feed it the URL to a more recent Pyodide and it got stuck in a bug loop which I fixed by pasting the code into a fresh session.

![Screenshot of the tool. APSW SQLite query explainer. Query is select * from sqlite_master where tbl_name = ? and a parameter box below is set to example. Below is JSON with the query and a bunch of details about it.](https://static.simonwillison.net/static/2025/apsw-explain.jpg)

[#](https://simonwillison.net/2025/Feb/7/apsw-sqlite-query-explainer/) [7th February 2025](https://simonwillison.net/2025/Feb/7/), [2 am](https://simonwillison.net/2025/Feb/7/apsw-sqlite-query-explainer/) / [pyodide](https://simonwillison.net/tags/pyodide/), [sqlite](https://simonwillison.net/tags/sqlite/), [claude](https://simonwillison.net/tags/claude/), [ai](https://simonwillison.net/tags/ai/), [llms](https://simonwillison.net/tags/llms/), [claude-artifacts](https://simonwillison.net/tags/claude-artifacts/), [webassembly](https://simonwillison.net/tags/webassembly/), [ai-assisted-programming](https://simonwillison.net/tags/ai-assisted-programming/), [python](https://simonwillison.net/tags/python/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [apsw](https://simonwillison.net/tags/apsw/)

**[llm-anthropic](https://github.com/simonw/llm-anthropic)**. I've renamed my [llm-claude-3](https://github.com/simonw/llm-claude-3) plugin to `llm-anthropic`, on the basis that Claude 4 will probably happen at some point so this is a better name for the plugin.

If you're a previous user of `llm-claude-3` you can upgrade to the new plugin like this:

```
llm install -U llm-claude-3
```

This should remove the old plugin and install the new one, because the latest `llm-claude-3` depends on `llm-anthropic`. Just installing `llm-anthropic` may leave you with both plugins installed at once.

There is one extra manual step you'll need to take during this upgrade: creating a new `anthropic` stored key with the same API token you previously stored under `claude`. You can do that like so:

```
llm keys set anthropic --value "$(llm keys get claude)"
```

I released [llm-anthropic 0.12](https://github.com/simonw/llm-anthropic/releases/tag/0.12) yesterday with new features not previously included in `llm-claude-3`:

> - Support for Claude's [prefill](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prefill-claudes-response) feature, using the new `-o prefill '{'` option and the accompanying `-o hide_prefill 1` option to prevent the prefill from being included in the output text. [#2](https://github.com/simonw/llm-anthropic/issues/2)
> - New `-o stop_sequences '```'` option for specifying one or more stop sequences. To specify multiple stop sequences pass a JSON array of strings :`-o stop_sequences '["end", "stop"]`.
> - Model options are now documented in the README.

If you install or upgrade `llm-claude-3` you will now get `llm-anthropic` instead, thanks to a tiny package on PyPI which depends on the new plugin name. I created that with my [pypi-rename](https://github.com/simonw/pypi-rename) cookiecutter template.

Here's the [issue for the rename](https://github.com/simonw/llm-claude-3/issues/31). I archived the [llm-claude-3 repository on GitHub](https://github.com/simonw/llm-claude-3), and got to use the brand new [PyPI archiving feature](https://simonwillison.net/2025/Jan/30/pypi-now-supports-project-archival/) to archive the [llm-claude-3 project on PyPI](https://pypi.org/project/llm-claude-3/) as well.

[#](https://simonwillison.net/2025/Feb/2/llm-anthropic/) [2nd February 2025](https://simonwillison.net/2025/Feb/2/), [6:17 am](https://simonwillison.net/2025/Feb/2/llm-anthropic/) / [llm](https://simonwillison.net/tags/llm/), [anthropic](https://simonwillison.net/tags/anthropic/), [claude](https://simonwillison.net/tags/claude/), [plugins](https://simonwillison.net/tags/plugins/), [ai](https://simonwillison.net/tags/ai/), [pypi](https://simonwillison.net/tags/pypi/), [llms](https://simonwillison.net/tags/llms/), [python](https://simonwillison.net/tags/python/), [generative-ai](https://simonwillison.net/tags/generative-ai/)

**[Latest black (25.1.0) adds a newline after docstring and before pass in an exception class](https://github.com/psf/black/issues/4571)**. I filed a bug report against Black when the latest release - 25.1.0 - reformatted the following code to add an ugly (to me) newline between the docstring and the `pass`:

```
class ModelError(Exception):
    "Models can raise this error, which will be displayed to the user"

    pass
```

Black maintainer Jelle Zijlstra confirmed that this is intended behavior with respect to [Black's 2025 stable style](https://github.com/psf/black/issues/4522), but also helped me understand that the `pass` there is actually unnecessary so I can fix the aesthetics by [removing that entirely](https://github.com/simonw/llm/commit/deb8bc3b4f5219583009eeb2c600d0b14c852c78).

I'm linking to this issue because it's a neat example of how I like to include steps-to-reproduce using [uvx](https://docs.astral.sh/uv/guides/tools/) to create one-liners you can paste into a terminal to see the bug that I'm reporting. In this case I shared the following:

> Here's a way to see that happen using `uvx`. With the previous Black version:
> 
> ```
> echo 'class ModelError(Exception):
>     "Models can raise this error, which will be displayed to the user"
>     pass' | uvx --with 'black==24.10.0' black -
> ```
> 
> This outputs:
> 
> ```
> class ModelError(Exception):
>     "Models can raise this error, which will be displayed to the user"
>     pass
> All done! ✨ 🍰 ✨
> 1 file left unchanged.
> ```
> 
> But if you bump to `25.1.0` this happens:
> 
> ```
> echo 'class ModelError(Exception):
>     "Models can raise this error, which will be displayed to the user"
>     pass' | uvx --with 'black==25.1.0' black - 
> ```
> 
> Output:
> 
> ```
> class ModelError(Exception):
>     "Models can raise this error, which will be displayed to the user"
> 
>     pass
> reformatted -
> 
> All done! ✨ 🍰 ✨
> 1 file reformatted.
> ```

Via [David Szotten](https://fosstodon.org/@davidszotten/113928041285282786) I learned that you can use `uvx black@25.1.0` here instead.

[#](https://simonwillison.net/2025/Jan/31/black-newline-docstring/) [31st January 2025](https://simonwillison.net/2025/Jan/31/), [9:27 pm](https://simonwillison.net/2025/Jan/31/black-newline-docstring/) / [python](https://simonwillison.net/tags/python/), [black](https://simonwillison.net/tags/black/), [uv](https://simonwillison.net/tags/uv/)

**[The surprising way to save memory with BytesIO](https://pythonspeed.com/articles/bytesio-reduce-memory-usage/)** ([via](https://lobste.rs/s/gvhivz/surprising_way_save_memory_with_bytesio "lobste.rs")) Itamar Turner-Trauring explains that if you have a `BytesIO` object in Python calling `.read()` on it will create a full copy of that object, doubling the amount of memory used - but calling `.getvalue()` returns a `bytes` object that uses no additional memory, instead using copy-on-write.

`.getbuffer()` is another memory-efficient option but it returns a [memoryview](https://docs.python.org/3/library/stdtypes.html#memoryview) which has less methods than the `bytes` you get back from `.getvalue()`\- it doesn't have `.find()` for example.

[#](https://simonwillison.net/2025/Jan/31/save-memory-with-bytesio/) [31st January 2025](https://simonwillison.net/2025/Jan/31/), [3:57 am](https://simonwillison.net/2025/Jan/31/save-memory-with-bytesio/) / [python](https://simonwillison.net/tags/python/)

**[PyPI now supports project archival](https://blog.pypi.org/posts/2025-01-30-archival/)**. Neat new PyPI feature, similar to GitHub's [archiving repositories](https://docs.github.com/en/repositories/archiving-a-github-repository/archiving-repositories) feature. You can now mark a PyPI project as "archived", making it clear that no new releases are planned (though you can switch back out of that mode later if you need to).

I like the sound of these future plans around this topic:

> Project archival is the first step in a larger project, aimed at improving the *lifecycle* of projects on PyPI. That project includes evaluating additional project statuses (things like "deprecated" and "unmaintained"), as well as changes to [PyPI's public APIs](https://docs.pypi.org/api/) that will enable clients to retrieve and act on project status information. You can track our progress on these fronts by following along with [warehouse#16844](https://github.com/pypi/warehouse/issues/16844)!

[#](https://simonwillison.net/2025/Jan/30/pypi-now-supports-project-archival/) [30th January 2025](https://simonwillison.net/2025/Jan/30/), [4:46 pm](https://simonwillison.net/2025/Jan/30/pypi-now-supports-project-archival/) / [psf](https://simonwillison.net/tags/psf/), [pypi](https://simonwillison.net/tags/pypi/), [python](https://simonwillison.net/tags/python/)

> We’re building a new static type checker for Python, from scratch, in Rust. From a technical perspective, it’s probably our most ambitious project yet. We’re about [800 PRs deep](https://github.com/astral-sh/ruff/pulls?q=is%3Aopen+is%3Apr+label%3Ared-knot)!
> 
> Like Ruff and uv, there will be a significant focus on performance. The entire system is designed to be highly incremental so that it can eventually power a language server (e.g., only re-analyze affected files on code change). \[...\]
> 
> We haven't publicized it to-date, but all of this work has been happening in the open, in the Ruff repository.

— [Charlie Marsh](https://bsky.app/profile/crmarsh.com/post/3lgvhzdfrps26)

[#](https://simonwillison.net/2025/Jan/29/charlie-marsh/) [29th January 2025](https://simonwillison.net/2025/Jan/29/), [6:53 pm](https://simonwillison.net/2025/Jan/29/charlie-marsh/) / [charlie-marsh](https://simonwillison.net/tags/charlie-marsh/), [rust](https://simonwillison.net/tags/rust/), [python](https://simonwillison.net/tags/python/), [uv](https://simonwillison.net/tags/uv/), [ruff](https://simonwillison.net/tags/ruff/), [astral](https://simonwillison.net/tags/astral/)

### [A selfish personal argument for releasing code as Open Source](https://simonwillison.net/2025/Jan/24/selfish-open-source/)

[![Visit A selfish personal argument for releasing code as Open Source](https://static.simonwillison.net/static/2025/E_236_Podcast_Title.jpg)](https://simonwillison.net/2025/Jan/24/selfish-open-source/)

I’m the guest for the most recent episode of the Real Python podcast with Christopher Bailey, talking about [Using LLMs for Python Development](https://realpython.com/podcasts/rpp/236/). We covered a *lot* of other topics as well—most notably my relationship with Open Source development over the years.

\[... [464 words](https://simonwillison.net/2025/Jan/24/selfish-open-source/)\]

**[uv python install --reinstall 3.13](https://twitter.com/charliermarsh/status/1876696188130394372)**. I couldn't figure out how to upgrade the version of Python 3.13 I had previous installed using `uv` - I had Python 3.13.0.rc2. Thanks to Charlie Marsh I learned the command for upgrading to the latest uv-supported release:

```
uv python install --reinstall 3.13
```

I can confirm it worked using:

```
uv run --python 3.13 python -c 'import sys; print(sys.version)'
```

Caveat from Zanie Blue on [my PR to document this](https://github.com/astral-sh/uv/pull/10377#issuecomment-2576353887):

> There are some caveats we'd need to document here, like this will break existing tool installations (and other virtual environments) that depend on the version. You'd be better off doing `uv python install 3.13.X` to add the new patch version in addition to the existing one.

[#](https://simonwillison.net/2025/Jan/7/uv-python-reinstall/) [7th January 2025](https://simonwillison.net/2025/Jan/7/), [8:43 pm](https://simonwillison.net/2025/Jan/7/uv-python-reinstall/) / [uv](https://simonwillison.net/tags/uv/), [charlie-marsh](https://simonwillison.net/tags/charlie-marsh/), [python](https://simonwillison.net/tags/python/)

**[Can LLMs write better code if you keep asking them to “write better code”?](https://minimaxir.com/2025/01/write-better-code/)** ([via](https://bsky.app/profile/minimaxir.bsky.social/post/3lern74vc5k2f "@minimaxir.bsky.social")) Really fun exploration by Max Woolf, who started with a prompt requesting a medium-complexity Python challenge - "`Given a list of 1 million random integers between 1 and 100,000, find the difference between the smallest and the largest numbers whose digits sum up to 30`" - and then continually replied with "`write better code`" to see what happened.

It works! Kind of... it's not quite as simple as "each time round you get better code" - the improvements sometimes introduced new bugs and often leaned into more verbose enterprisey patterns - but the model (Claude in this case) did start digging into optimizations like numpy and numba JIT compilation to speed things up.

I used to find the thing where telling an LLM to "do better" worked completely surprising. I've since come to terms with why it works: LLMs are effectively stateless, so each prompt you execute is considered as an entirely new problem. When you say "write better code" your prompt is accompanied with a copy of the previous conversation, so you're effectively saying "here is some code, suggest ways to improve it". The fact that the LLM itself wrote the previous code isn't really important.

I've been having a lot of fun recently using LLMs for cooking inspiration. "Give me a recipe for guacamole", then "make it tastier" repeated a few times results in some bizarre and fun variations on the theme!

[#](https://simonwillison.net/2025/Jan/3/asking-them-to-write-better-code/) [3rd January 2025](https://simonwillison.net/2025/Jan/3/), [6 pm](https://simonwillison.net/2025/Jan/3/asking-them-to-write-better-code/) / [max-woolf](https://simonwillison.net/tags/max-woolf/), [prompt-engineering](https://simonwillison.net/tags/prompt-engineering/), [ai-assisted-programming](https://simonwillison.net/tags/ai-assisted-programming/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [ai](https://simonwillison.net/tags/ai/), [llms](https://simonwillison.net/tags/llms/), [python](https://simonwillison.net/tags/python/)

### 2024

**[Open WebUI](https://github.com/open-webui/open-webui)**. I tried out this open source (MIT licensed, JavaScript and Python) localhost UI for accessing LLMs today for the first time. It's very nicely done.

I ran it with [uvx](https://docs.astral.sh/uv/guides/tools/) like this:

```
uvx --python 3.11 open-webui serve
```

On first launch it installed a bunch of dependencies and then downloaded 903MB to `~/.cache/huggingface/hub/models--sentence-transformers--all-MiniLM-L6-v2` - a copy of the [all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) embedding model, presumably for its [RAG feature](https://docs.openwebui.com/features/rag).

It then presented me with a working Llama 3.2:3b chat interface, which surprised me because I hadn't spotted it downloading that model. It turns out that was because I have [Ollama](https://ollama.com/) running on my laptop already (with several models, including Llama 3.2:3b, already installed) - and Open WebUI automatically detected Ollama and gave me access to a list of available models.

I found a "knowledge" section and added all of the Datasette documentation (by dropping in the `.rst` files from the docs) - and now I can type `#` in chat to search for a file, add that to the context and then ask questions about it directly.

I selected the `spatialite.rst.txt` file, prompted it with "How do I use SpatiaLite with Datasette" and got back [this](https://gist.github.com/simonw/3bf5ff0ed3b47aefbb94d3fd992f81f9#response):

![Chat UI. Prompt is How do I use SpatiaLite with Datasette? with an attached spatialite.rst.txt file. The response from llama3.2:3b reads: To use SpatiaLite with Datasette, you need to install the mod_spatialite dynamic library. This can then be loaded into Datasette using the --load-extension command-line option.   You can install it on OS X by running brew update and then brew install spatialite-tools. On Linux, SpatiaLite is packaged for most distributions, so you can typically install it with a package manager like apt.   When running Datasette, you can look for SpatiaLite in common installation locations or specify the full path to the extension if it's installed elsewhere.   For example, on OS X, you might run datasette --load-extension=spatialite after installing it with Homebrew. On Linux, you could use datasette --load-extension=/usr/lib/x86_64-linux-gnu/mod_spatialite.so.   It's also important to note that SpatiaLite adds a large number of additional SQL functions, some of which are not safe for untrusted users to execute. To secure your Datasette instance, consider disabling arbitrary SQL queries and defining canned queries with the SQL queries that use SpatiaLite functions you want people to be able to execute.](https://static.simonwillison.net/static/2024/spatialite-webui.jpg)

That's honestly a very solid answer, especially considering the Llama 3.2 3B model from Ollama is just a 1.9GB file! It's impressive how well that model can handle basic Q&A and summarization against text provided to it - it somehow has a 128,000 token context size.

Open WebUI has a lot of other tricks up its sleeve: it can talk to API models such as OpenAI directly, has optional integrations with web search and custom tools and logs every interaction to a SQLite database. It also comes with [extensive documentation](https://docs.openwebui.com/).

[#](https://simonwillison.net/2024/Dec/27/open-webui/) [27th December 2024](https://simonwillison.net/2024/Dec/27/), [1:38 am](https://simonwillison.net/2024/Dec/27/open-webui/) / [ollama](https://simonwillison.net/tags/ollama/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [llama](https://simonwillison.net/tags/llama/), [ai](https://simonwillison.net/tags/ai/), [rag](https://simonwillison.net/tags/rag/), [llms](https://simonwillison.net/tags/llms/), [uv](https://simonwillison.net/tags/uv/), [sqlite](https://simonwillison.net/tags/sqlite/), [python](https://simonwillison.net/tags/python/), [edge-llms](https://simonwillison.net/tags/edge-llms/)

### [Trying out QvQ—Qwen’s new visual reasoning model](https://simonwillison.net/2024/Dec/24/qvq/)

[![Visit Trying out QvQ - Qwen's new visual reasoning model](https://static.simonwillison.net/static/2024/count-pelicans-easy.jpg)](https://simonwillison.net/2024/Dec/24/qvq/)

I thought we were done for major model releases in 2024, but apparently not: Alibaba’s Qwen team just dropped the ~~Apache 2.0 licensed~~ Qwen licensed ([the license changed](https://simonwillison.net/2024/Dec/24/qvq/#the-license-changed)) QvQ-72B-Preview, “an experimental research model focusing on enhancing visual reasoning capabilities”.

\[... [1,838 words](https://simonwillison.net/2024/Dec/24/qvq/)\]

**[Finally, a replacement for BERT: Introducing ModernBERT](https://www.answer.ai/posts/2024-12-19-modernbert.html)** ([via](https://bsky.app/profile/benjaminwarner.dev/post/3ldur45oz322b "@benjaminwarner.dev")) [BERT](https://en.wikipedia.org/wiki/BERT_\(language_model\)) was an early language model released by Google in October 2018. Unlike modern LLMs it wasn't designed for generating text. BERT was trained for masked token prediction and was generally applied to problems like Named Entity Recognition or Sentiment Analysis. BERT also wasn't very useful on its own - most applications required you to fine-tune a model on top of it.

In exploring BERT I decided to try out [dslim/distilbert-NER](https://huggingface.co/dslim/distilbert-NER), a popular Named Entity Recognition model fine-tuned on top of DistilBERT (a smaller distilled version of the original BERT model). [Here are my notes](https://til.simonwillison.net/llms/bert-ner) on running that using `uv run`.

Jeremy Howard's [Answer.AI](https://www.answer.ai/) research group, [LightOn](https://www.lighton.ai/) and friends supported the development of ModernBERT, a brand new BERT-style model that applies many enhancements from the past six years of advances in this space.

While BERT was trained on 3.3 billion tokens, producing 110 million and 340 million parameter models, ModernBERT trained on 2 trillion tokens, resulting in 140 million and 395 million parameter models. The parameter count hasn't increased much because it's designed to run on lower-end hardware. It has a 8192 token context length, a significant improvement on BERT's 512.

I was able to run one of the demos from the announcement post using `uv run` like this (I'm not sure why I had to use `numpy<2.0` but without that I got an error about `cannot import name 'ComplexWarning' from 'numpy.core.numeric'`):

```
uv run --with 'numpy<2.0' --with torch --with 'git+https://github.com/huggingface/transformers.git' python
```

Then this Python:

```
import torch
from transformers import pipeline
from pprint import pprint
pipe = pipeline(
    "fill-mask",
    model="answerdotai/ModernBERT-base",
    torch_dtype=torch.bfloat16,
)
input_text = "He walked to the [MASK]."
results = pipe(input_text)
pprint(results)
```

Which downloaded 573MB to `~/.cache/huggingface/hub/models--answerdotai--ModernBERT-base` and output:

```
[{'score': 0.11669921875,
  'sequence': 'He walked to the door.',
  'token': 3369,
  'token_str': ' door'},
 {'score': 0.037841796875,
  'sequence': 'He walked to the office.',
  'token': 3906,
  'token_str': ' office'},
 {'score': 0.0277099609375,
  'sequence': 'He walked to the library.',
  'token': 6335,
  'token_str': ' library'},
 {'score': 0.0216064453125,
  'sequence': 'He walked to the gate.',
  'token': 7394,
  'token_str': ' gate'},
 {'score': 0.020263671875,
  'sequence': 'He walked to the window.',
  'token': 3497,
  'token_str': ' window'}]
```

I'm looking forward to trying out models that use ModernBERT as their base. The model release is accompanied by a paper ([Smarter, Better, Faster, Longer: A Modern Bidirectional Encoder for Fast, Memory Efficient, and Long Context Finetuning and Inference](https://arxiv.org/abs/2412.13663)) and [new documentation](https://huggingface.co/docs/transformers/main/en/model_doc/modernbert) for using it with the Transformers library.

[#](https://simonwillison.net/2024/Dec/24/modernbert/) [24th December 2024](https://simonwillison.net/2024/Dec/24/), [6:21 am](https://simonwillison.net/2024/Dec/24/modernbert/) / [ai](https://simonwillison.net/tags/ai/), [jeremy-howard](https://simonwillison.net/tags/jeremy-howard/), [transformers](https://simonwillison.net/tags/transformers/), [hugging-face](https://simonwillison.net/tags/hugging-face/), [uv](https://simonwillison.net/tags/uv/), [python](https://simonwillison.net/tags/python/), [nlp](https://simonwillison.net/tags/nlp/), [bert](https://simonwillison.net/tags/bert/)

### [Building Python tools with a one-shot prompt using uv run and Claude Projects](https://simonwillison.net/2024/Dec/19/one-shot-python-tools/)

[![Visit Building Python tools with a one-shot prompt using uv run and Claude Projects](https://static.simonwillison.net/static/2024/s3-debug-social-media-card.jpg)](https://simonwillison.net/2024/Dec/19/one-shot-python-tools/)

I’ve written a lot about how I’ve been using Claude to build one-shot HTML+JavaScript applications [via Claude Artifacts](https://simonwillison.net/tags/claude-artifacts/). I recently started using a similar pattern to create one-shot Python utilities, using a custom Claude Project combined with the dependency management capabilities of [uv](https://github.com/astral-sh/uv).

\[... [899 words](https://simonwillison.net/2024/Dec/19/one-shot-python-tools/)\]

**[Phi-4 Technical Report](https://arxiv.org/abs/2412.08905)** ([via](https://twitter.com/peteratmsr/status/1867375567739482217 "@peteratmsr")) Phi-4 is the latest LLM from Microsoft Research. It has 14B parameters and claims to be a big leap forward in the overall Phi series. From [Introducing Phi-4: Microsoft’s Newest Small Language Model Specializing in Complex Reasoning](https://techcommunity.microsoft.com/blog/aiplatformblog/introducing-phi-4-microsoft%E2%80%99s-newest-small-language-model-specializing-in-comple/4357090):

> Phi-4 outperforms comparable and larger models on math related reasoning due to advancements throughout the processes, including the use of high-quality synthetic datasets, curation of high-quality organic data, and post-training innovations. Phi-4 continues to push the frontier of size vs quality.

The model is currently available [via Azure AI Foundry](https://ai.azure.com/explore/models/Phi-4/version/1/registry/azureml). I couldn't figure out how to access it there, but Microsoft are planning to release it via Hugging Face in the next few days. It's not yet clear what license they'll use - hopefully MIT, as used by the previous models in the series.

In the meantime, unofficial GGUF versions have shown up on Hugging Face already. I got one of the [matteogeniaccio/phi-4](https://huggingface.co/matteogeniaccio/phi-4/tree/main) GGUFs working with my [LLM](https://llm.datasette.io/) tool and [llm-gguf plugin](https://github.com/simonw/llm-gguf) like this:

```
llm install llm-gguf
llm gguf download-model https://huggingface.co/matteogeniaccio/phi-4/resolve/main/phi-4-Q4_K_M.gguf
llm chat -m gguf/phi-4-Q4_K_M
```

This downloaded a 8.4GB model file. Here are some initial [logged transcripts](https://gist.github.com/simonw/0235fd9f8c7809d0ae078495dd630b67) I gathered from playing around with the model.

An interesting detail I spotted on the Azure AI Foundry page is this:

> Limited Scope for Code: Majority of phi-4 training data is based in Python and uses common packages such as `typing`, `math`, `random`, `collections`, `datetime`, `itertools`. If the model generates Python scripts that utilize other packages or scripts in other languages, we strongly recommend users manually verify all API uses.

This leads into the most interesting thing about this model: the way it was trained on synthetic data. The technical report has a *lot* of detail about this, including this note about why synthetic data can provide better guidance to a model:

> Synthetic data as a substantial component of pretraining is becoming increasingly common, and the Phi series of models has consistently emphasized the importance of synthetic data. Rather than serving as a cheap substitute for organic data, synthetic data has several direct advantages over organic data.
> 
> **Structured and Gradual Learning**. In organic datasets, the relationship between tokens is often complex and indirect. Many reasoning steps may be required to connect the current token to the next, making it challenging for the model to learn effectively from next-token prediction. By contrast, each token generated by a language model is by definition predicted by the preceding tokens, making it easier for a model to follow the resulting reasoning patterns.

And this section about their approach for generating that data:

> Our approach to generating synthetic data for phi-4 is guided by the following principles:
> 
> 1. Diversity: The data should comprehensively cover subtopics and skills within each domain. This requires curating diverse seeds from organic sources.
> 2. Nuance and Complexity: Effective training requires nuanced, non-trivial examples that reflect the complexity and the richness of the domain. Data must go beyond basics to include edge cases and advanced examples.
> 3. Accuracy: Code should execute correctly, proofs should be valid, and explanations should adhere to established knowledge, etc.
> 4. Chain-of-Thought: Data should encourage systematic reasoning, teaching the model various approaches to the problems in a step-by-step manner. \[...\]
> 
> We created 50 broad types of synthetic datasets, each one relying on a different set of seeds and different multi-stage prompting procedure, spanning an array of topics, skills, and natures of interaction, accumulating to a total of about 400B unweighted tokens. \[...\]
> 
> **Question Datasets**: A large set of questions was collected from websites, forums, and Q&A platforms. These questions were then filtered using a plurality-based technique to balance difficulty. Specifically, we generated multiple independent answers for each question and applied majority voting to assess the consistency of responses. We discarded questions where all answers agreed (indicating the question was too easy) or where answers were entirely inconsistent (indicating the question was too difficult or ambiguous). \[...\]
> 
> **Creating Question-Answer pairs from Diverse Sources**: Another technique we use for seed curation involves leveraging language models to extract question-answer pairs from organic sources such as books, scientific papers, and code.

[#](https://simonwillison.net/2024/Dec/15/phi-4-technical-report/) [15th December 2024](https://simonwillison.net/2024/Dec/15/), [11:58 pm](https://simonwillison.net/2024/Dec/15/phi-4-technical-report/) / [llm](https://simonwillison.net/tags/llm/), [phi](https://simonwillison.net/tags/phi/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [training-data](https://simonwillison.net/tags/training-data/), [ai](https://simonwillison.net/tags/ai/), [microsoft](https://simonwillison.net/tags/microsoft/), [llms](https://simonwillison.net/tags/llms/), [ai-assisted-programming](https://simonwillison.net/tags/ai-assisted-programming/), [python](https://simonwillison.net/tags/python/)

**[googleapis/python-genai](https://github.com/googleapis/python-genai)**. Google released this brand new Python library for accessing their generative AI models yesterday, offering an alternative to their existing [generative-ai-python](https://github.com/google-gemini/generative-ai-python) library.

The API design looks very solid to me, and it includes both sync and async implementations. Here's an async streaming response:

```
async for response in client.aio.models.generate_content_stream(
    model='gemini-2.0-flash-exp',
    contents='Tell me a story in 300 words.'
):
    print(response.text)
```

It also includes Pydantic-based output schema support and some nice syntactic sugar for defining tools using Python functions.

[#](https://simonwillison.net/2024/Dec/12/python-genai/) [12th December 2024](https://simonwillison.net/2024/Dec/12/), [4:21 pm](https://simonwillison.net/2024/Dec/12/python-genai/) / [async](https://simonwillison.net/tags/async/), [gemini](https://simonwillison.net/tags/gemini/), [google](https://simonwillison.net/tags/google/), [python](https://simonwillison.net/tags/python/), [pydantic](https://simonwillison.net/tags/pydantic/), [llms](https://simonwillison.net/tags/llms/), [ai](https://simonwillison.net/tags/ai/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [llm-tool-use](https://simonwillison.net/tags/llm-tool-use/)

### [ChatGPT Canvas can make API requests now, but it’s complicated](https://simonwillison.net/2024/Dec/10/chatgpt-canvas/)

[![Visit ChatGPT Canvas can make API requests now, but it's complicated](https://static.simonwillison.net/static/2024/run-python-code.jpg)](https://simonwillison.net/2024/Dec/10/chatgpt-canvas/)

Today’s [12 Days of OpenAI](https://openai.com/12-days/?day=4) release concerned [ChatGPT Canvas](https://help.openai.com/en/articles/9930697-what-is-the-canvas-feature-in-chatgpt-and-how-do-i-use-it), a new ChatGPT feature that enables ChatGPT to pop open a side panel with a shared editor in it where you can collaborate with ChatGPT on editing a document or writing code.

\[... [1,116 words](https://simonwillison.net/2024/Dec/10/chatgpt-canvas/)\]

**[Introducing Limbo: A complete rewrite of SQLite in Rust](https://turso.tech/blog/introducing-limbo-a-complete-rewrite-of-sqlite-in-rust)** ([via](https://news.ycombinator.com/item?id=42378843 "Hacker News")) This looks absurdly ambitious:

> Our goal is to build a reimplementation of SQLite from scratch, fully compatible at the language and file format level, with the same or higher reliability SQLite is known for, but with full memory safety and on a new, modern architecture.

The Turso team behind it have been maintaining their [libSQL](https://github.com/tursodatabase/libsql) fork for two years now, so they're well equipped to take on a challenge of this magnitude.

SQLite is justifiably famous for its [meticulous approach to testing](https://www.sqlite.org/testing.html). Limbo plans to take an entirely different approach based on "Deterministic Simulation Testing" - a modern technique [pioneered by FoundationDB](https://antithesis.com/blog/is_something_bugging_you/) and now spearheaded by [Antithesis](https://antithesis.com/), the company Turso have been working with on their previous testing projects.

Another bold claim (emphasis mine):

> We have both added DST facilities to the core of the database, and partnered with Antithesis to achieve a level of reliability in the database that lives up to SQLite’s reputation.
> 
> \[...\] With DST, **we believe we can achieve an even higher degree of robustness than SQLite**, since it is easier to simulate unlikely scenarios in a simulator, test years of execution with different event orderings, and upon finding issues, reproduce them 100% reliably.

The two most interesting features that Limbo is planning to offer are first-party WASM support and fully asynchronous I/O:

> SQLite itself has a synchronous interface, meaning driver authors who want asynchronous behavior need to have the extra complication of using helper threads. Because SQLite queries tend to be fast, since no network round trips are involved, a lot of those drivers just settle for a synchronous interface. \[...\]
> 
> Limbo is designed to be asynchronous from the ground up. It extends `sqlite3_step`, the main entry point API to SQLite, to be asynchronous, allowing it to return to the caller if data is not ready to consume immediately.

[Datasette](https://datasette.io/) provides an [async API](https://docs.datasette.io/en/stable/internals.html#await-db-execute-sql) for executing SQLite queries which is backed by all manner of complex thread management - I would be very interested in a native asyncio Python library for talking to SQLite database files.

I successfully tried out Limbo's [Python bindings](https://github.com/tursodatabase/limbo/tree/main/bindings/python) against a demo SQLite test database using `uv` like this:

```
uv run --with pylimbo python
>>> import limbo
>>> conn = limbo.connect("/tmp/demo.db")
>>> cursor = conn.cursor()
>>> print(cursor.execute("select * from foo").fetchall())
```

It crashed when I tried against a more complex SQLite database that included SQLite FTS tables.

The Python bindings aren't yet documented, so I piped them through [LLM](https://llm.datasette.io/) and had the new `google-exp-1206` model write [this initial documentation](https://gist.github.com/simonw/bd1822f372c406d17ed24772f8b93eea) for me:

```
files-to-prompt limbo/bindings/python -c | llm -m gemini-exp-1206 -s 'write extensive usage documentation in markdown, including realistic usage examples'
```

[#](https://simonwillison.net/2024/Dec/10/introducing-limbo/) [10th December 2024](https://simonwillison.net/2024/Dec/10/), [7:25 pm](https://simonwillison.net/2024/Dec/10/introducing-limbo/) / [rust](https://simonwillison.net/tags/rust/), [sqlite](https://simonwillison.net/tags/sqlite/), [uv](https://simonwillison.net/tags/uv/), [open-source](https://simonwillison.net/tags/open-source/), [python](https://simonwillison.net/tags/python/), [llm](https://simonwillison.net/tags/llm/), [ai-assisted-programming](https://simonwillison.net/tags/ai-assisted-programming/), [documentation](https://simonwillison.net/tags/documentation/), [limbo](https://simonwillison.net/tags/limbo/)

### [I can now run a GPT-4 class model on my laptop](https://simonwillison.net/2024/Dec/9/llama-33-70b/)

[![Visit I can now run a GPT-4 class model on my laptop](https://static.simonwillison.net/static/2024/livebench-llama.jpg)](https://simonwillison.net/2024/Dec/9/llama-33-70b/)

Meta’s new [Llama 3.3 70B](https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct) is a genuinely GPT-4 class Large Language Model that runs on my laptop.

\[... [2,905 words](https://simonwillison.net/2024/Dec/9/llama-33-70b/)\]

**[Transferring Python Build Standalone Stewardship to Astral](https://gregoryszorc.com/blog/2024/12/03/transferring-python-build-standalone-stewardship-to-astral/)**. Gregory Szorc's [Python Standalone Builds](https://github.com/indygreg/python-build-standalone) have been [quietly running](https://xkcd.com/2347/) an increasing portion of the Python ecosystem for a few years now, but really accelerated in importance when [uv](https://github.com/astral-sh/uv) started using them for new Python installations managed by that tool. The releases (shipped via GitHub) have now been downloaded over 70 million times, 50 million of those since uv's initial release in March of this year.

uv maintainers Astral have been helping out with PSB maintenance for a while:

> When I told Charlie I could use assistance supporting PBS, Astral employees started contributing to the project. They have built out various functionality, including Python 3.13 support (including free-threaded builds), turnkey automated release publishing, and debug symbol stripped builds to further reduce the download/install size. Multiple Astral employees now have GitHub permissions to approve/merge PRs and publish releases. All [releases](https://github.com/indygreg/python-build-standalone/releases) since April have been performed by Astral employees.

As-of December 17th Gregory will be transferring the project to the Astral organization, while staying on as a maintainer and advisor. Here's Astral's post about this: [A new home for python-build-standalone](https://astral.sh/blog/python-build-standalone).

[#](https://simonwillison.net/2024/Dec/3/python-build-standalone-astral/) [3rd December 2024](https://simonwillison.net/2024/Dec/3/), [11:18 pm](https://simonwillison.net/2024/Dec/3/python-build-standalone-astral/) / [uv](https://simonwillison.net/tags/uv/), [astral](https://simonwillison.net/tags/astral/), [python](https://simonwillison.net/tags/python/)

**[PydanticAI](https://ai.pydantic.dev/)** ([via](https://twitter.com/pydantic/status/1863538947059544218 "@pydantic")) New project from Pydantic, which they describe as an "Agent Framework / shim to use Pydantic with LLMs".

I asked [which agent definition they are using](https://twitter.com/simonw/status/1863567881553977819) and it's the "system prompt with bundled tools" one. To their credit, they explain that [in their documentation](https://ai.pydantic.dev/agents/):

> The [Agent](https://ai.pydantic.dev/api/agent/) has full API documentation, but conceptually you can think of an agent as a container for:
> 
> - A [system prompt](https://ai.pydantic.dev/agents/#system-prompts) — a set of instructions for the LLM written by the developer
> - One or more [retrieval tool](https://ai.pydantic.dev/agents/#function-tools) — functions that the LLM may call to get information while generating a response
> - An optional structured [result type](https://ai.pydantic.dev/results/) — the structured datatype the LLM must return at the end of a run

Given how many other existing tools already lean on Pydantic to help define JSON schemas for talking to LLMs this is an interesting complementary direction for Pydantic to take.

There's some overlap here with my own [LLM](https://llm.datasette.io/) project, which I still hope to add a function calling / tools abstraction to in the future.

[#](https://simonwillison.net/2024/Dec/2/pydanticai/) [2nd December 2024](https://simonwillison.net/2024/Dec/2/), [9:08 pm](https://simonwillison.net/2024/Dec/2/pydanticai/) / [llm](https://simonwillison.net/tags/llm/), [python](https://simonwillison.net/tags/python/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [llms](https://simonwillison.net/tags/llms/), [pydantic](https://simonwillison.net/tags/pydantic/), [llm-tool-use](https://simonwillison.net/tags/llm-tool-use/), [ai-agents](https://simonwillison.net/tags/ai-agents/)

**[SmolVLM—small yet mighty Vision Language Model](https://huggingface.co/blog/smolvlm)**. I've been having fun playing with this new vision model from the Hugging Face team behind [SmolLM](https://simonwillison.net/2024/Nov/2/smollm2/). They describe it as:

> \[...\] a 2B VLM, SOTA for its memory footprint. SmolVLM is small, fast, memory-efficient, and fully open-source. All model checkpoints, VLM datasets, training recipes and tools are released under the Apache 2.0 license.

I've tried it in a few flavours but my favourite so far is the [mlx-vlm](https://github.com/Blaizzy/mlx-vlm) approach, via `mlx-vlm` author [Prince Canuma](https://twitter.com/Prince_Canuma/status/1862168514842280401). Here's the `uv` recipe I'm using to run it:

```
uv run \
  --with mlx-vlm \
  --with torch \
  python -m mlx_vlm.generate \
    --model mlx-community/SmolVLM-Instruct-bf16 \
    --max-tokens 500 \
    --temp 0.5 \
    --prompt "Describe this image in detail" \
    --image IMG_4414.JPG
```

If you run into an error using Python 3.13 (torch compatibility) try `uv run --python 3.11` instead.

This one-liner installs the necessary dependencies, downloads the model (about 4.2GB, saved to `~/.cache/huggingface/hub/models--mlx-community--SmolVLM-Instruct-bf16`) and executes the prompt and displays the result.

I ran that against [this Pelican photo](https://static.simonwillison.net/static/2024/IMG_4414.JPG):

![A glorious pelican on some rocks, two other pelicans are visible plus some other birds](https://static.simonwillison.net/static/2024/IMG_4414.JPG)

The model replied:

> In the foreground of this photograph, a pelican is perched on a pile of rocks. The pelican’s wings are spread out, and its beak is open. There is a small bird standing on the rocks in front of the pelican. The bird has its head cocked to one side, and it seems to be looking at the pelican. To the left of the pelican is another bird, and behind the pelican are some other birds. The rocks in the background of the image are gray, and they are covered with a variety of textures. The rocks in the background appear to be wet from either rain or sea spray.

There are a few spatial mistakes in that description but the vibes are generally in the right direction.

On my 64GB M2 MacBook pro it read the prompt at 7.831 tokens/second and generated that response at an impressive 74.765 tokens/second.

[#](https://simonwillison.net/2024/Nov/28/smolvlm/) [28th November 2024](https://simonwillison.net/2024/Nov/28/), [8:29 pm](https://simonwillison.net/2024/Nov/28/smolvlm/) / [vision-llms](https://simonwillison.net/tags/vision-llms/), [uv](https://simonwillison.net/tags/uv/), [mlx](https://simonwillison.net/tags/mlx/), [ai](https://simonwillison.net/tags/ai/), [edge-llms](https://simonwillison.net/tags/edge-llms/), [llms](https://simonwillison.net/tags/llms/), [python](https://simonwillison.net/tags/python/), [generative-ai](https://simonwillison.net/tags/generative-ai/), [smollm](https://simonwillison.net/tags/smollm/)