# rhythmic
Fluent Regex builder for node.js

When completed, this project will allow for a fluent interface for building regular expressions. For now, this is a placeholder. :)

```javascript
var rhy = require("rhythmic");
var anything_but_pipe_or_quote = "[^\\|'\"`]*";
var params = (index) => rhy.capture(rhy.zero_or_more(rhy.nonCapturingGroup(anything_but_pipe_or_quote + rhy.optional(rhy.quoted(".*?",index)))));
var parenthetical_params = rhy.nonCapturingGroup(rhy.parenthetical(params(2)));
var comma_params = rhy.nonCapturingGroup("," + params(5));
var pipe_params = rhy.choice_of(parenthetical_params, comma_params);
var pipe_expression = rhy.capture(rhy.identifier()) + rhy.space() + rhy.optional(rhy.nonCapturingGroup(pipe_params));
var pipe_symbol = "\\|";
var pattern = rhy.nonCapturingGroup(pipe_symbol + rhy.space() + pipe_expression + rhy.space());
```
