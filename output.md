AIMessage {
  lc_serializable: true,
  lc_kwargs: {
    content: "I don't like Mondays.",
    additional_kwargs: { function_call: undefined }
  },
  lc_namespace: [ 'langchain', 'schema' ],
  content: "I don't like Mondays.",
  name: undefined,
  additional_kwargs: { function_call: undefined }
}
 node index.js
I don't like Mondays.
undefined
 lalit@lalitnayyar-ausus13  ~  OneDrive  Scrimba1  bawlrunnablesequence  main 
❯ node index.js
StringPromptValue {
  lc_serializable: false,
  lc_kwargs: 'Given a sentence correct the grammar.\n' +
    "    sentence: I don't liked Mondays.\n" +
    '    sentence with correct grammar: \n' +
    '    ',
  lc_namespace: [ 'langchain', 'prompts', 'base' ],
  value: 'Given a sentence correct the grammar.\n' +
    "    sentence: I don't liked Mondays.\n" +
    '    sentence with correct grammar: \n' +
    '    '
}
 lalit@lalitnayyar-ausus13  ~  OneDrive  Scrimba1  bawlrunnablesequence  main 
❯ node index.js
I don't like Mondays.
 lalit@lalitnayyar-ausus13  ~  OneDrive  Scrimba1  bawlrunnablesequence  main 
❯