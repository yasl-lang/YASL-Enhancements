# Pattern Matching

A new keyword `match` needs to be added, as well as syntax for pattern matching.

The syntax is as follows:

```
match_stmt  = "match" expr "{" (patterns ("if" expr)? "{" stmt* "}")* "}";
match_expr  = "match" expr "{" (patterns ("if" expr)? "=>" expr)* "}";
patterns    = pattern ("|" pattern)*;
pattern     = range | table_pat | list_pat | literal_pat | binding_pat;
range       = int ":" int;
table_pat   = "{" (literal_pat ":" pattern),* ("," "...")? "}";
list_pat    = "[" pattern,* ("," "...")? "]";
literal_pat = str | int | float | bool | undef | table | list | fn;
binding_pat = ("const" | "let") id ("=" pattern)? | "_";
```

precedence needs to be cleared up slightly here, but this should be a solid base for patterns.
