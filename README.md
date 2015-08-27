# PageDown

Linux, OSX: [![Build Status](https://api.travis-ci.org/wookay/PageDown.jl.svg?branch=master)](https://travis-ci.org/wookay/PageDown.jl)
Windows: [![Build status](https://ci.appveyor.com/api/projects/status/61g3ch0ba6fafvmy?svg=true)](https://ci.appveyor.com/project/wookay/PageDown.jl)
[![Coverage Status](https://coveralls.io/repos/wookay/PageDown.jl/badge.svg?branch=master&service=github)](https://coveralls.io/github/wookay/PageDown.jl?branch=master)

# install
```shell
λ ~$ julia
               _
   _       _ _(_)_     |  A fresh approach to technical computing
  (_)     | (_) (_)    |  Documentation: http://docs.julialang.org
   _ _   _| |_  __ _   |  Type "?help" for help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 0.4.0-dev+7032 (2015-08-27 04:01 UTC)
 _/ |\__'_|_|_|\__'_|  |  Commit 5d3ccd6 (0 days old master)
|__/                   |  x86_64-apple-darwin14.5.0

julia> Pkg.clone("git@github.com:wookay/PageDown.jl.git")
INFO: Cloning PageDown from git@github.com:wookay/PageDown.jl.git
INFO: Computing changes...

julia> using PageDown
INFO: Recompiling stale cache file /Users/wookyoung/.julia/lib/v0.4/PageDown.ji for module PageDown.
```

# examples
```shell
julia> using PageDown

julia> using Base.Markdown

julia> pages = [
         md"""
         # hello
          - 1
          - 2
         """

         md"""
         # world
          - 3
         """

         md"""
         # julia
          - 123
         """
       ]
     hello
    ≡≡≡≡≡≡≡

    •  1
    •  2
     world
    ≡≡≡≡≡≡≡

    •  3
     julia
    ≡≡≡≡≡≡≡

    •  123

julia> page = Page(pages)
PageDown.Page([Base.Markdown.MD(Any[Base.Markdown.Header{1}(Any["hello"]),Base.Markdown.List(Any[Any["1"],Any["2"]],false)],Dict{Any,Any}(:config=>Base.Markdown.Config([hashheader,fencedcode,blockquote],[blocktex,blockinterp,list,indentcode,github_table,horizontalrule,setextheader,paragraph],Dict('['=>[link],'\\'=>[linebreak,escapes],'*'=>[asterisk_bold,asterisk_italic],'$'=>[tex,interp],'`'=>[inline_code],'!'=>[image],'-'=>[en_dash])))),Base.Markdown.MD(Any[Base.Markdown.Header{1}(Any["world"]),Base.Markdown.List(Any[Any["3"]],false)],Dict{Any,Any}(:config=>Base.Markdown.Config([hashheader,fencedcode,blockquote],[blocktex,blockinterp,list,indentcode,github_table,horizontalrule,setextheader,paragraph],Dict('['=>[link],'\\'=>[linebreak,escapes],'*'=>[asterisk_bold,asterisk_italic],'$'=>[tex,interp],'`'=>[inline_code],'!'=>[image],'-'=>[en_dash])))),Base.Markdown.MD(Any[Base.Markdown.Header{1}(Any["julia"]),Base.Markdown.List(Any[Any["123"]],false)],Dict{Any,Any}(:config=>Base.Markdown.Config([hashheader,fencedcode,blockquote],[blocktex,blockinterp,list,indentcode,github_table,horizontalrule,setextheader,paragraph],Dict('['=>[link],'\\'=>[linebreak,escapes],'*'=>[asterisk_bold,asterisk_italic],'$'=>[tex,interp],'`'=>[inline_code],'!'=>[image],'-'=>[en_dash]))))],1,1,Dict{Any,Any}(),3)

julia> @current
     hello
    ≡≡≡≡≡≡≡

    •  1
    •  2

julia> @page
1:1:3

julia> @next

     world
    ≡≡≡≡≡≡≡

    •  3

julia> @next

     julia
    ≡≡≡≡≡≡≡

    •  123

julia> @prev
     world
    ≡≡≡≡≡≡≡

    •  3

julia> @first
     hello
    ≡≡≡≡≡≡≡

    •  1
    •  2

julia> @last
     julia
    ≡≡≡≡≡≡≡

    •  123

julia> @step 2
2

julia> @first
     hello
    ≡≡≡≡≡≡≡

    •  1
    •  2
     world
    ≡≡≡≡≡≡≡

    •  3

julia> @next

     julia
    ≡≡≡≡≡≡≡

    •  123
```
