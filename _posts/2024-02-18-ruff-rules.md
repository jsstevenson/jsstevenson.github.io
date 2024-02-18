---
layout: post
title: "Some personal favorites from newly-implemented Ruff rules"
categories: ["python", "dev tools"]
---

[Ruff](https://docs.astral.sh/ruff) has taken Python linting and formatting by storm, consolidating a wide array of Python CI tools under the mantle of a single library (this has [not come without controversy](https://www.youtube.com/watch?v=XzW4-KEB664)). They make their case based on speed, but for my money, the real killer feature is the centralization: everything is included -- optionally -- under one roof, with no need to hunt for external libraries (we had a case recently where two ``flake8`` plugins had mutually exclusive dependencies, which was a real headache). They've been reimplementing rules from existing linting packages at a breakneck pace, and I recently went through some of the latest additions while updating our lab's [Python library template](https://github.com/GenomicMedLab/software-templates). In doing so, I actually learned a lot of new things about the Python language itself -- here are some of my new favorites:

### [flake8-logging-format](https://docs.astral.sh/ruff/rules/#flake8-logging-format-g)

I never really bothered learning much of the standard lib logging module, because it's [such a headache](https://news.ycombinator.com/item?id=31949003). That said, there were some simple goofs I was stuck on, such as errantly using f-strings when lazy strings would do ([``G004``](https://docs.astral.sh/ruff/rules/logging-f-string/)).

### [flake8-print](https://docs.astral.sh/ruff/rules/#flake8-print-t20)

This is me. I do this all the time. It's embarrassing. But, no more.

### [flake8-pytest-style](https://docs.astral.sh/ruff/rules/#flake8-pytest-style-pt)

What I learned from running this on our codebase was how little I knew about default args in core `pytest` methods. I do think newer users would benefit a lot from checks like [``PT017``](https://docs.astral.sh/ruff/rules/pytest-assert-in-except/), which forces use of `pytest.raises()` to check for exceptions.

### [flake8-simplify](https://docs.astral.sh/ruff/rules/#flake8-simplify-sim)

Lots of great checks for Pythonic-ness here. In particular, I hadn't known about [``contextlib.suppress``](https://docs.python.org/3/library/contextlib.html#contextlib.suppress), which is preferred in [``SIM105``](https://docs.astral.sh/ruff/rules/suppressible-exception/).

### [flake8-use-pathlib](https://docs.astral.sh/ruff/rules/#flake8-use-pathlib-pth)

I've been on the [``pathlib``](https://docs.python.org/3/library/pathlib.html) train for a while, but I didn't realize how extensive its feature set is. In particular, [``pth123``](https://docs.astral.sh/ruff/rules/builtin-open/) is a big deviation from a lot of standard Python boilerplate.

### [Ruff-specific rules](https://docs.astral.sh/ruff/rules/#ruff-specific-rules-ruf)

I think most of these are great, and that they're fixable is awesome, too. The type conversion syntax required in [``RUF010``](https://docs.astral.sh/ruff/rules/explicit-f-string-type-conversion/) was new to me. [``RUF019``](https://docs.astral.sh/ruff/rules/unnecessary-key-check/) is great for catching a common beginner mistake from new contributors. [``RUF027``](https://docs.astral.sh/ruff/rules/missing-f-string-syntax/) is a smart one to try to catch, although I could foresee a lot of false positives.
