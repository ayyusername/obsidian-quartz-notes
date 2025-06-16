@ LAWXER, we killed the “layout” chunking approach from the very beginning because our goal was to build something that is capable of understanding the semantics/data independently from its form. So, all application workflows were aimed at repeating the human understanding and analysis workflows, where only raw data was available in the form of a flat text string (totally unformatted). We took this approach to be able to use the same engine to use speech as input (no formatting in speech) in future development.

Relying on data format to analyze its composition will block you in the future because the engine will be built around the format (or to require format) and not the pure data (in any format).

https://weaviate.io/developers/weaviate/quickstart Vector database
