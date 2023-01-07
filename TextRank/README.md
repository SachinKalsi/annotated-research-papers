# TextRank: Bringing Order into Texts

TextRank is a graph based algorithm to fetch the important keyword phrases or sentences from the text corpus

Original Paper link: https://aclanthology.org/W04-3252/

## Summary of the paper (How TextRank works?)
1. It’s all about applying graph-based algorithm to natural language & extracting keyword phrases or sentences.
2. Each vertex in the graph can either be a word or a sentence and the graph-based ranking model assigns the score to each vertex
3. When one vertex links to another one (depending on the window size `N`), it is casting a vote for that other vertex & the higher the number of votes a vertex gets, the higher the importance of the vertex.
4. Keyword Extraction
    1. Vertices are words
    2. 2 vertices (words) are connected if they co-occur within a window of maximum `N` words (from 2 to 10 words)
6. Sentence Extraction
    1. Vertices are sentences
    2. 2 vertices (sentences) are connected depending on the similarity (similarity could be cosine, jaccard, no. of common noun words etc)
    3. The co-occurrence relation used for keyword extraction cannot be applied here for sentence extraction.
    4. The text is therefore represented as a **weighted graph**, and the weighted graph-based ranking algorithm has been used
8. The graph-based ranking algorithm is run on the graph for several iterations until it converges – usually for 20-30 iterations, at a threshold of 0.0001
    
## Annotation standards

🟡 - The important research or study with respect to the core concept explained in the paper are highlighted in yellow 🟡 color.

🟢 - The important takeways or learnings are highlighted in green 🟢 color

`Underline` - mini conlusions or crisp summary found in the paper are underlined
