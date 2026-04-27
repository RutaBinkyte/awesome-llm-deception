# Contribution Guidelines

Thank you for considering a contribution to **Awesome LLM Deception Research**. This list exists to be a high-quality, focused resource — not an exhaustive index. Please read these guidelines carefully before opening a pull request.

## What belongs here

A paper is a good candidate if it meets **all** of the following:

- It studies deception, honesty, alignment faking, or mechanistic interpretability of deceptive representations in language models.
- It has an empirical component (experiments, benchmarks, probing results, or human evaluations). Purely theoretical or position papers do not qualify.
- It has been posted to arXiv, published at a peer-reviewed venue, or released as a technical report by a research institution.
- It is the best or one of the best resources on its specific topic — not just another paper in the area.

## What does not belong here

- Survey papers (unless they are uniquely comprehensive and widely cited — the bar is high).
- Papers on general LLM safety, RLHF, or alignment that do not specifically study deception or honesty representations.
- Blog posts, Twitter threads, or non-peer-reviewed opinion pieces.
- Duplicates of already-listed work.

## Formatting rules

These are enforced by [awesome-lint](https://github.com/sindresorhus/awesome-lint), so please follow them exactly or your PR will fail the linter check.

- Add your entry to the most relevant existing section.
- Within a section, entries should be in roughly chronological order (oldest first).
- Use this exact format:

```
- [Title](URL) - One-sentence description that starts with an uppercase letter and ends with a period.
```

- The description should describe the *paper*, not the list entry. Do not start with "A paper that…" or "This work…".
- Do not include the authors' names in the description — put them in parentheses after, like the existing entries.
- Keep descriptions to one sentence. If you cannot summarize it in one sentence, it may not be focused enough for this list.

## How to add a paper

1. Fork this repository.
2. Add your entry in the appropriate section of `README.md`.
3. Run `npx awesome-lint` locally and fix any reported issues before opening your PR.
4. Open a pull request with the title `Add [Paper Short Name]`.
5. In the PR body, briefly explain why this paper meets the criteria above and what it adds that is not already covered.

## Reviewing pull requests

If you open a PR, you are expected to review at least two other open PRs in good faith — point out formatting issues, assess whether the paper meets the criteria, or suggest description improvements. This keeps the list self-sustaining.

## Questions

Open an issue if you are unsure whether a paper qualifies before spending time on a PR.
