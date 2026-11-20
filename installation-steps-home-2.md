# Installation steps: home-2

Release home-2's adoption and read-back's setup at work, in order. Each step names the conversation or place it goes into. Paste each prompt as it stands.

## W0.1, by hand, at work, in the browser

Signed in to GitHub, open the release repository's page, then Code, then Download ZIP. Don't open or extract it.

## W0.2, by hand, in VS Code at work

In the work harness's own window, start a new Claude Code conversation and rename it before typing anything:

```
(Release Two) Ready Check
```

## W0.3, type into (Release Two) Ready Check

The Ready Check prompt:

```text
This is a check before adopting a release into this harness. Read only: write nothing anywhere, change no setting, and run every git command with --no-optional-locks, since a plain git status can rewrite the index. Check this harness and its release history, found through the root map. One, outstanding work: every path git status --porcelain names, tracked or untracked; name each to me here, but count them in the result line. Two, line-ending-only files: tracked files whose bytes differ from their HEAD blob and equal it once every carriage return before a line feed is removed. Three, stale index entries: files git diff-files --name-only lists whose raw hash, git hash-object --no-filters, equals their HEAD blob. Four, locks: any file ending in .lock under either repository's git folder, and whether any git process is running. Five, download marks: files in this harness's tree that carry a Zone.Identifier stream, with adopt-release's check-release.ps1 named apart. Six, what the adoption expects: the release history has one commit, home-1, no remote key and core.autocrlf false; this harness's core.autocrlf is false; the ledger's last entry is home-1 and records an overlay for project-files/read-back; the root map has no row for the dependency archive; and adopt-release's SKILL.md and check-release.ps1 hash to 3f74075221a9bc228eb3868ad79201ba25b438dbbab5b0979287b13b642fed04 and 179e717511a7af17b17844d1fbdb71035afb67d1a129677e26aaa18c9f684171. End with one line per check, numbered one to six, each with its count or pass or fail. Name no overlay, person, client or path of this harness in those lines.
```

## W0.4, by hand, check, in (Release Two) Ready Check

Its last reply gives its result lines. If it names outstanding work, close the session that owns that work with close-session, then run W0.2 and W0.3 again in a new conversation:

```
(Release Two) Ready Check 2
```

If it names line-ending-only files, stale entries or a lock, run W0.5 to W0.7. If it names nothing, go to W0.8.

## W0.5, by hand, in VS Code at work

**Only if Ready Check names line-ending-only files, stale entries or a lock.** Start a new conversation in the work harness's window and rename it:

```
(Release Two) Put Back
```

## W0.6, type into (Release Two) Put Back

**Only if Ready Check names line-ending-only files, stale entries or a lock.** The Put Back prompt, with the counts Ready Check gave:

```text
This is a step before adopting a release into this harness, for only what the readiness check named. Commit nothing and change no setting. Run every git read with --no-optional-locks, and every git command that writes on its own, with nothing chained after it; if one fails, tell me and stop. First, if the check named a lock, show me the lock and whether any git process is running, and remove it only on my yes. Then, for each line-ending-only file, prove again that its bytes with every carriage return before a line feed removed equal its HEAD blob, show me the list, and on my yes write each one's HEAD blob over it with git cat-file blob, in Bash, never PowerShell. Then, for every file git diff-files --name-only lists, compare its raw hash, git hash-object --no-filters, with its HEAD blob. If any doesn't match, name it and refresh nothing. If every one matches, ask my yes, then run git update-index -q --refresh on its own, never git add. Then show me that git diff-files and git status both name nothing. End with counts: locks removed, files put back, files proved, and whether the refresh ran. Name no overlay, person, client or path of this harness in those lines.
```

## W0.7, answer in (Release Two) Put Back

**Only if Ready Check names line-ending-only files, stale entries or a lock.** Yes to each list it shows, if it holds only what Ready Check named; otherwise no, and stop. Its last reply gives its counts.

## W0.8, by hand, in VS Code at work

Start a new conversation in the work harness's window and rename it:

```
(Release Two) Unpack home-2
```

## W0.9, type into (Release Two) Unpack home-2

The Unpack prompt. Its last reply gives the unpacked folder and its counts.

```text
This is a step before adopting a release, outside this harness. Write nothing in this harness or its release history, and run nothing from the download. The release I downloaded is the newest ZIP in my Downloads folder whose name starts with method-releases-. Read whether it carries a Zone.Identifier stream, then clear it with Unblock-File, and read it again. Then extract it with Expand-Archive into a new empty folder in my Downloads folder, named release-home-2 with today's date. Then check the folder holds exactly one entry, a folder, whose manifest.md reads "- Release: home-2", and count the files under it and how many carry a Zone.Identifier stream. End with the folder's full path, so I can give it to the adoption, and the counts: marked before, marked after, files extracted, files marked.
```

## W0.10, by hand, in VS Code at work

Start a new conversation in the work harness's window and rename it:

```
(Release Two) Adopt home-2
```

## W0.11, type into (Release Two) Adopt home-2

The Adopt prompt, with the folder Unpack gave in place of the bracket:

```text
Adopt the release I unpacked into [the folder Unpack gave], with adopt-release from this harness's skills folder. This is a later adoption: home-1 is in the ledger. Run each git command that writes on its own, with nothing chained to run after it, whether it succeeds or fails; if one fails, tell me and stop. Run git reads with --no-optional-locks.
```

## W0.12, answer in (Release Two) Adopt home-2

Each question, as you choose; install nothing; at every permission prompt, a one-time yes, never "don't ask again".

## W0.13, by hand, check, in (Release Two) Adopt home-2, before you approve

How the install preview names read-back's installs' item, for W-preview: `project-files/read-back`, or `read-back`. Either way, go on.

## W0.14, by hand, check, in (Release Two) Adopt home-2, after your answers

Whether it reports a collide it didn't report before your answers. If it does, check nothing of the harness's is overwritten, and stop it before the commit if anything would be. Its last reply says it committed `Adopt home-2`, or where it stopped, and names the decisions with no record.

## W0.15, by hand, in VS Code at work

Start a new conversation in the work harness's window and rename it:

```
(Release Two) Work Records
```

## W0.16, type into (Release Two) Work Records

The Work Records prompt. Answer each record's draft as you choose.

```text
Release home-2 is adopted, and read-back's files are in its overlay, but nothing of read-back's is set up. Before setup, write three records through this harness's own decision skill, under this harness's own numbers, each on my yes by that skill's steps. Never cite an upstream decision by its number. Each record carries one line, Answers upstream, listing in quotation marks, exactly as home-2's manifest writes them under Decisions relied on, the upstream titles it answers. First, the basis decision: it accepts read-back's loopback-only link listener as built and its two per-user Windows entries as built, and it's the basis for bringing read-back's four engine parts in and running its setup, because installing tools here is monitored, not strictly governed. Each part comes from its publisher first, and only where a publisher no longer serves it, from the upstream dependency archive, downloaded by hand in the browser, read-only, with nothing going back. This harness doesn't take up the archive method itself until the release that carries it. It answers "Read-back may run a loopback-only link listener", "Read-back may register two per-user Windows entries that outlive sessions" and "Public parts come from their publishers first". Second, a narrow exception for the one ONNX advisory, on the same grounds as the upstream harness's and ending on the same condition, read from read-back's it-response.md in its placed folder, which is the answer if IT asks. It answers "Read-back may carry onnxruntime with one ONNX advisory open". Third, the same for the one sherpa-onnx CVE. It answers "Read-back may carry sherpa-onnx with one open CVE". Neither exception loosens the rule that nothing adopted here carries a known flaw IT would find, for any other part. End with each record's title and the titles it answers. Name no person or client.
```

## W0.17, by hand, in VS Code at work

Start a new conversation in the work harness's window and rename it:

```
(Release Two) Set Up Read-back
```

## W0.18, type into (Release Two) Set Up Read-back

The Set Up prompt, with the comparison filled as not yet run:

```text
Set up read-back in its overlay, by its own setup steps as home-2 carries them: its README's Setup section and setup/engine.md. First, check this harness's decisions folder: each of these five titles must appear in quotation marks in one record's Answers upstream line: "Read-back may run a loopback-only link listener", "Read-back may register two per-user Windows entries that outlive sessions", "Read-back may carry onnxruntime with one ONNX advisory open", "Read-back may carry sherpa-onnx with one open CVE" and "Public parts come from their publishers first". If one is missing, name it and stop. Check it-response.md is in read-back's placed folder. Then draft a root-map row, the dependency archive, with the value method-dependencies, the archive repository's name as the upstream role map gives it, and write it only on my yes, since every session here loads that map; name the change. Then, before I download, show me any file in my Downloads folder already holding one of the four recorded download names, and on my yes move them into a new folder there. Give me each part's link in setup/engine.md's order, publisher first. For onnxruntime 1.28.3, its recorded link first: my opening it now is the re-check, and its source follows from what it does. For comparison only, the upstream read on 2026-11-26 found: not yet run. Where a link doesn't serve its part, I download the same file from the dependency archive's release for that part and version. When I say I've downloaded, read each download's Zone.Identifier host only, then run place-engine.ps1. If it stops on a mismatch, place nothing, tell me which part, and stop: that's a route question for the upstream harness. Then the Visual C++ runtime check, then install.ps1 in Windows PowerShell from read-back's folder. Then draft the three hook registrations for this harness's root .claude/settings.json, as the README gives them, and write them only on my yes. Run each git command that writes on its own, with nothing chained after it, and git reads with --no-optional-locks. After I say how a play went, read the events log for that job's onnxruntime-loaded line. End with the steps done and their results, naming no overlay, person, client or path of this harness.
```

## W0.19, answer in (Release Two) Set Up Read-back

Yes or no to the map row and to moving any same-named downloads aside, as you choose.

## W0.20, by hand, in the browser at work

For each of the four parts, in the order the session gives, open the link it gives. For onnxruntime, open the recorded link first, and note what it did for W-link: [it downloaded a file | it said not found | other: ____]. Where a part's link doesn't serve it, download the same file from the dependency archive's release for that part and version. Each is saved in Downloads under its recorded name.

From the dependency archive's release, take the file named after the release's tag, not Source code zip or tar.gz.

## W0.21, type into (Release Two) Set Up Read-back

Choose one option in each bracket:

```text
Downloaded. onnxruntime's recorded link: [downloaded a file | said not found | other: ____]. Anti-virus: [nothing raised | something raised | other: ____].
```

## W0.22, answer in (Release Two) Set Up Read-back

Yes or no to the three hook registrations it drafts.

## W0.23, by hand, in VS Code at work

In any work conversation at the harness's root, end a turn, then click its play link or its notification. Listen.

## W0.24, type into (Release Two) Set Up Read-back

Choose one option:

```text
Played: [in the Kokoro voice | said Kokoro is unavailable | didn't open | other: ____].
```

## W0.24a, type into (Release Two) Set Up Read-back

It runs close-session, which commits the map row and the settings file with its note. Check its last reply says it's closed and committed.

```text
close
```

## W0.25, by hand, in VS Code at work

Start a new conversation in the work harness's window and rename it:

```
(Release Two) Check home-2
```

## W0.26, type into (Release Two) Check home-2

The Check prompt. Its last reply gives sixteen lines, W1 to W16. Type nothing more into it.

```text
Check the adoption of release home-2 and read-back's setup in this harness. Read only: write nothing, change no setting, run every git command with --no-optional-locks and none that could reach a remote. Read today's transcripts of this harness's Ready Check, Put Back if it ran, Unpack home-2, Adopt home-2, Work Records and Set Up Read-back conversations, the harness, its release history, the unpacked folder, the decisions folder, the settings files and read-back's events log. Then give one line per check, in the form W1 pass or W1 fail, with the counts asked for, and nothing else. Name no overlay, person, client, record number or path of this harness in those lines.
W1: the adoption made exactly one commit, message exactly Adopt home-2 with no other line, and the only commits between Ready Check's HEAD and it were made for outstanding work by the session that owned it; the release history has exactly two commits, home-1 then home-2; the ledger's last entry is home-2; the adoption used this harness's own adopt-release, asked no overlay question for an item home-1's ledger entry records, and wrote nothing before my answers; neither config has a remote key.
W2: the sort ran with home-1's manifest piped in as the base and gave each file same, replace or add by its change since home-1, or keep or merge where the ledger names it as this harness's own; give the count of each, and say whether both adopt-release files were same. Every file home-2 ships hashes at its place to the manifest, apart from files the ledger names as kept or merged.
W3: Unpack unblocked the ZIP before extracting it, and no extracted file carries a Zone.Identifier stream; the adoption's download check printed ok the first time; nothing in the adoption's conversation unblocked a file or wrote outside the harness and the release history. Give the count extracted and the count marked.
W4: Ready Check ran only reads, every git command with --no-optional-locks, and wrote nothing; give its counts. If it named outstanding work, that work was committed by its own session before the adoption, and the adoption's commit holds none of it. If it named nothing, no Put Back and no refresh ran before the adoption.
W5: if Put Back ran, each listed file was proved against its HEAD blob before any refresh, the refresh ran only after all matched and on my yes, as git update-index -q --refresh, and diff-files and status then named nothing. If it didn't run, say not run.
W6: in every one of those conversations, each git command that writes ran on its own with nothing chained after it, any failure was reported and stopped the session, no file ending in .lock is in either git folder now, and any lock found was removed only on my yes after showing no git process ran.
W7: for each file the Adopt home-2 commit modified that home-2 doesn't ship, git diff numstat between that commit and its parent equals the same with ignore-cr-at-eol. Give the count checked and the count that differ.
W8: the adoption named each title in home-2's Decisions relied on with no record here and wrote nothing to the decisions folder; give the count named and how many were read-back's. The three new records were committed after Adopt home-2 and before setup's first step.
W9: each of read-back's five titles appears in quotation marks in exactly one record's Answers upstream line; the basis decision's names the listener's, the Windows entries' and Public parts come from their publishers first, and records the upstream dependency archive as the fallback source; no record names an upstream decision by its number.
W10: each exception, read beside it-response.md, covers its one flaw only, rests on the same grounds as the upstream harness's and ends on the same condition, and neither loosens the rule that nothing adopted here carries a known flaw IT would find, for any other part.
W11: setup found all five titles and it-response.md, hashing as the manifest gives it, before its first step; the root map holds one dependency-archive row, written after my yes and before the first archive download, named in that session's reply and its close; the adoption's commit didn't change the root map.
W12: each download came from its publisher where the publisher served it and from the dependency archive where it didn't, by its Zone.Identifier host only; place-engine.ps1 printed that all four downloads match and placed seven files at their recorded SHA-256s, or stopped on a mismatch and placed nothing; nothing was uploaded. Say which of the three onnxruntime outcomes it was.
W13: the Visual C++ runtime check found it; install.ps1 ran; reg query finds HKCU\Software\Classes\readback and HKCU\Software\Classes\AppUserModelId\ReadBack; bin holds the launcher and the hotkey library.
W14: the three hook registrations were shown to me, then written to the root settings file only after my yes; that file names stop-hook, session-start-sweep and prompt-submit-hook once each; no other settings file names them.
W15: a job after setup in read-back's events log has onnxruntime-loaded with engine sherpa-kokoro, version 1.28.3, and a path ending in read-back's own engine\lib\onnxruntime.dll, before that job's job-start.
W16: every git command ran on the harness or the release history, none could reach a remote, and no web tool was called in the adoption.
```
