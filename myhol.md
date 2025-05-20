build utop with bellow modification

```diff
diff --git a/src/lib/uTop.ml b/src/lib/uTop.ml
index 801fd29..ecb686e 100644
--- a/src/lib/uTop.ml
+++ b/src/lib/uTop.ml
@@ -305,7 +305,7 @@ let parse_default parse str eos_is_error =
     | exn ->
         Error ([], "Unknown parsing error (please report it to the utop project): " ^ Printexc.to_string exn)

-let parse_toplevel_phrase_default = parse_default Parse.toplevel_phrase
+let parse_toplevel_phrase_default = fun str -> parse_default !Toploop.parse_toplevel_phrase str
 let parse_toplevel_phrase = ref parse_toplevel_phrase_default

 let parse_use_file_default = parse_default Parse.use_file
```

build hol with `HOLLIGHT_USE_MODULE=1 make`
