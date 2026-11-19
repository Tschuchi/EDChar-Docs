# CLAUDE.md as a working contract

Claude Code reads the file `CLAUDE.md` in the project folder at the start of every session. In EDChar each instance has its own CLAUDE.md. It works like a contract: it defines the role, what the instance may and may not do, how it works with the board, and which commands it understands. Thore Schuchardt says what changes, the instance writes it down.

## Size and history

Status on 2026-11-19 (counted):

| Instance | Lines | Commits to CLAUDE.md |
|---|---:|---:|
| Frontend | 161 | 24 |
| Backend | 207 | 33 |
| Testing | 146 | 17 |
| Board-Keeper | 153 | 22 |
| Docs | 76 | 3 |

The files started small on 2026-06-27 with a few notes on the shell environment. Most rules were added later, in response to incidents. See [Rules and why they exist](rules.md).

## What a CLAUDE.md contains

The headings differ between instances, but the same building blocks appear in all of them:

| Building block | Example (shortened, translated) |
|---|---|
| **Role** | "Your only task is to keep the ticket board up to date." (Board-Keeper) |
| **May / may not** | "Does not touch source code, neither frontend nor backend." (Testing) |
| **Environment** | Build and live addresses, the shell (Windows PowerShell, no heredocs), how to work with paths outside the own folder |
| **Hard rules** | "The Dart side uses camelCase, the PHP backend uses snake_case. This is not converted automatically." (Frontend) |
| **Board procedure** | Which lines and files the instance may change, pull before and push after every change |
| **Commands** | `scan` for all instances; `GoLive` for Backend; `Ticket Status` for the Board-Keeper; `Docs veröffentlichen` (publish docs) for Docs |
| **Evidence** | Label every finding as "observed" or "derived from the code" |
| **Before finishing a task** | Frontend: run `flutter analyze`, check field names against the API contract, update README and docs in the same commit |
| **Changes to this file** | See below |

## Who changes the contract

Frontend, Backend and Testing follow the same rule since 2026-11-05, Docs since its start. The Board-Keeper may change its CLAUDE.md when Thore Schuchardt gives an instruction.

> Changes to this CLAUDE.md that implement an instruction from Thore are committed without asking. The instance's own rule changes, without an instruction from Thore, are presented to him first.

An instance therefore does not add rules for itself without approval. Thore Schuchardt gives the instruction, and the instance phrases the rule in its own file.

## CLAUDE.md and the board

The frontend CLAUDE.md puts the relation like this:

> Before every scan, first check the own CLAUDE.md for current rules. CLAUDE.md is the source of truth for the workflow, the board is only the task list.

The rules of the board itself are in the board's protocol file, which each CLAUDE.md refers to. Rules that apply to one instance are only in its own file.

## Public versions

The CLAUDE.md files of the other instances contain server details and other internal information and are not published. This website only shows shortened, translated excerpts with comments.
