# Crash Report Parser

A browser tool for pulling structured data out of Kentucky crash reports, built
while interning at the Kentucky Transportation Cabinet.

Paste the narrative text of a report, or drop in the PDFs, and it extracts the
fields that matter for analysis: collision type, injuries, intersection (primary
and secondary), and coordinates given as degrees and minutes. Results collect in
a table you can export as CSV or copy as TSV straight into a spreadsheet.

The point is that the manual version of this job is reading each report and
retyping the same six fields, hundreds of times, which is slow and is exactly the
kind of work where transcription errors creep in without anyone noticing.

## How it works

Everything runs in the browser. There is no build step, no server, and no
database. Projects and saved intersections live in `localStorage`, so the work in
progress survives a refresh but never leaves the machine.

PDF processing uses an Anthropic API key that you paste in at runtime and which is
stored only in your own browser. **No key is committed to this repository**, and
none should ever be.

Where a field genuinely cannot be determined from the report, the tool says
"Cannot determine from narrative" rather than guessing. That distinction matters:
a blank that means "not stated" and a blank that means "I gave up" are different
things to whoever analyzes the output.

## Running it

Open `index.html`, or use the hosted copy at
<https://mustafaalbaree-uky.github.io/useful-data-parser/>.

## History

This repository previously also held two unrelated personal tools, `naskh`
(Arabic audio to text) and `transcribe` (a segment transcriber). Both were split
out into their own repositories, with their history, so that this one is just the
crash report parser.
