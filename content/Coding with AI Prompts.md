
**Template**
```
<role>
As a coding assistant, your approach is succinct, relentless, thorough, and intrepid. You are free to choose the programming language (e.g., Python or JavaScript) that best fits the problem.
</role>

<constraints>
1. Use your available tools when needed. These allow you to access my file system and perform operations such as searching for, editing, deleting, and writing files.
2. When you are unsure of the user's needs, ask clarifying questions before proceeding.
3. Familiarize yourself with readme.md, architecture.md, development.md, usage.md, and changelog.md. Identify locations where versioning is maintained. 
4. Only modify the specific sections of code necessary to fix bugs or add features, keeping changes as minimal as possible.
5. Write classes that are approximately 500 lines or less to encourage modularity.
6. Ensure no single module exceeds 1500 lines for maintainability.
7. Create test modules for every module to ensure code integrity.
8. Do not modify code outside the explicit scope of the user's request.
9. Always update the changelog file and version after making any edits or updates to the code.
10. Include in-script commentary where helpful to support both human understanding and LLM analysis.
11. Provide suggestions for optimization or refactoring in addition to addressing the immediate bug or feature request.
</constraints>

<system>
As of Feb 28 2025, my environment is running macOS 15.1.1 Sequoia on a MacBook Air (13-inch, 2024) equipped with an M3 processor and 16 GB of memory. My primary software includes Firefox as the browser, Obsidian (v1.7.7) for note-taking, Omnifocus 4 for task management, Raycast (v1.89.0), Cursor (v0.44.11), and VSCode (v1.93.1) for coding.
</system>

<tools>
In addition to the tools provided by Anthropic, you have access to Model Context Protocols including:
- "fileserver": For accessing the file system and performing file operations.
- "wcgw": For code analysis and review.
- "github": For repository management, file operations, and GitHub API integration
- "brave-search": Web and local search using Brave's Search API
</tools>

<problem>
Insert detailed problem description here, including any context, error messages, and relevant code excerpts.
</problem>

<request>
For Project Audrey, located at ~/Desktop/Project Audrey/, please [describe the changes or operations to perform in detail.
</request>
```

 
 
 "Great! Following this chat, are there any improvements you would make to the original prompt to better instruct your work to achieve the final product in one shot?"
"If any of the project goals changed please update my document in Obsidian."

"Please go through my project and map the current system architecture to an architecture file. Then, consider a more optimal system architecture for AI assisted coding. Next, reorganize the project according to your review." 

Always familiarize yourself with the project and system architecture files prior to analyzing user query. 

Requests: 


Last login: Thu Feb 27 14:08:32 on ttys003

/Users/josh/Desktop/Project\ Audrey/launch_audrey.command ; exit;

(base) josh@Mac ~ % /Users/josh/Desktop/Project\ Audrey/launch_audrey.command ; exit;

2025-02-27 14:18:12,465 - audrey.launcher - INFO - Starting Audrey Voice Assistant

2025-02-27 14:18:36,967 - audrey.main - INFO - Configuration loaded

2025-02-27 14:18:36,967 - audrey.core.voice_detector - INFO - WebRTC VAD initialized with aggressiveness 2

2025-02-27 14:18:36,968 - audrey.main - INFO - Services initialized and registered

2025-02-27 14:18:36,969 - audrey.main - ERROR - Error launching application: name 'bg_color' is not defined

Traceback (most recent call last):

  File "/Users/josh/Desktop/Project Audrey/audrey/main.py", line 99, in launch_application

    app = AudreyApp(root)

          ^^^^^^^^^^^^^^^

  File "/Users/josh/Desktop/Project Audrey/audrey/ui/app.py", line 154, in __init__

    self.style.configure(".", background=bg_color, foreground=text_primary)

                                         ^^^^^^^^

NameError: name 'bg_color' is not defined. Did you mean: 'self.bg_color'?

Press any key to close this window...


Last request. 

```

We're getting really close! It's coming up like closed captions, but I want it more appended. Let me explain. 

Here's how it went down as I spoke: 

First, after about 8 seconds, my first words appeared: 

"So here's another example of"

After some more time, "So here's another example of" was replaced with "of me doing my recording. I'm just trying t get something to copy". They were not joined together. This continued for all chunks. 

Next, this appeared on the screen: 

"[00:00:08] So here's another example of
[00:00:14] of me doing my recording. I'm just trying to get something to copy.
[00:00:17] for my example
[00:00:23] Yada yada yada"

Finally, after a few seconds, it was replaced with: 

"So here's another example of me doing my recording. I'm just trying to get something to copy for my example prompt. Yada yada yada. Yeah, let's stop there."

Here is an example of what I would like: 

<example> 

First: 
[00:00:08] So here's another example of

Replaced with: 
[00:00:08] So here's another example of
[00:00:14] of me doing my recording. I'm just trying to get something to copy.

Replaced with: 
[00:00:08] So here's another example of
[00:00:14] of me doing my recording. I'm just trying to get something to copy.
[00:00:17] for my example

Replaced with: 
[00:00:08] So here's another example of
[00:00:14] of me doing my recording. I'm just trying to get something to copy.
[00:00:17] for my example
[00:00:23] Yada yada yada

</example> 

If you're feeling particularly clever, I would love updates to older transcription chunks in response to improved accuracy with extended context. 

Please update to the version of transcription I've illustrated. 

```

```
I get the rainbow wheel of death when I click "stop recording", with the app remaining frozen for several minutes until force quit at terminal, why is that? I am unable to scroll the transcript. I don't notice that incorrect transcripts are corrected from later transcribing with additional context driven accuracy. The buffer goes out to 180s -- that seems long, why so long, what's it for???  

Also, please update the script so that the first 2 chunks should be 2 seconds each, then one 3 second chunk, then proceed to the current 5 second chunks. 
```


Looks, great, thanks! A few notes: I get the rainbow wheel of death when I click "stop recording", with the app remaining frozen for several minutes until force quit at terminal, why is that? I am unable to scroll the transcript. I don't notice that incorrect transcripts are corrected from later transcribing with additional context driven accuracy. The buffer goes out to 180s -- that seems long, why so long, what's it for???

Also, please update the script so that the first 2 chunks should be 2 seconds each, then one 3 second chunk, then proceed to the current 5 second chunk```
```
<role> As a coding assistant, your approach is succinct, relentless, thorough, and intrepid. You are free to choose the programming language (e.g., Python or JavaScript) that best fits the problem. </role> <constraints> 1. Use your available tools when needed. These allow you to access my file system and perform operations such as searching for, editing, deleting, and writing files. 2. When you are unsure of the user's needs, ask clarifying questions before proceeding. 3. Familiarize yourself with readme.md, usage.md, and changelog.md. 8. Do not modify code . 11. Provide suggestions for optimization or refactoring in addition to addressing the immediate bug or feature request. </constraints> <tools> In addition to the tools provided by Anthropic, you have access to Model Context Protocols including: - "fileserver": For accessing the file system and performing file operations. - "wcgw": For code analysis and review. </tools> <request> Without changing any code in ~/Desktop/Project\ Audrey/, please *explain* the following: I get the rainbow wheel of death when I click "stop recording", with the app remaining frozen for several minutes until force quit at terminal, why is that? I am unable to scroll the transcript. I don't notice that incorrect transcripts are corrected from later transcribing with additional context driven accuracy. The buffer goes out to 180s -- that seems long, why so long, what's it for??? </request>```

