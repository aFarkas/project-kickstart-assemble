# Why Not?

## Why do you put `build/` under version control?

Wouldn't it be better to but them into `svn:ignore` or `.gitignore`?

Pre-build in VCS has the following advantages:

- You cannot guarantee, that the build will be exactly the same in the future (because of changing cli api's in node, grunt, sass etc.)
  - Another solution would be to put the distribution build on a build server.
- You have a pre build version in your version control system to show to the project manager / client


## Why don't you put `dist/` under version control, too?

Because each committed version, contains every source file and a fully updated build folder. The main difference between
dist and build is, that dist has production ready graphics and css/js files combined and so on.

Because you don't create releases that often, those are tasks for a release script, and should be made on a build server
or with an extra shell script.


## Why don't you remove the prefix from page, main, nav, header, aside, footer classes?

Because if we would use .header as class for the header, it would influence other .header elements of other
blocks. For instance:

```
CSS

.page
.header
.main
    .b-article
        .header
        .content
.footer
```

If we set color for `.header` now, we would have to reset it on `.b-article .header`.

Don't even think about abusing `.header[role=banner]` as excuse! Count: 1 (increment if you tried!). ;)