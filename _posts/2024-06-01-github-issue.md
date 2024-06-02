---
title: Github 블로그 세팅하면서 발생한 이슈
description: >-
  Github 블로그 만들면서 마주친 몇가지 이슈 정리
author: leesp2
date: 2024-06-01 19:36:00 +0900
categories: [Github blog]
tags: [getting started]
math: true
mermaid: true
---

github 블로그 만들면서 몇가지 삽질한 부분 정리


## timezone이슈
_config.yml에 timezone 값만 넣고 서버를 실행하면 다음과 같은 에러가 발생

```
$bundle exec jekyll serve
Configuration file: D:/git/leesp2.github.io/_config.yml
  Dependency Error: Yikes! It looks like you don't have tzinfo or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. If you've run Jekyll with `bundle exec`, ensure that you have included the tzinfo gem in your Gemfile as well. The full error message from Ruby is: 'cannot load such file -- tzinfo' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
jekyll 4.3.3 | Error:  tzinfo
C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/external.rb:70:in `rescue in block in require_with_graceful_fail': tzinfo (Jekyll::Errors::MissingDependencyException)
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/external.rb:56:in `block in require_with_graceful_fail'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/external.rb:55:in `each'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/external.rb:55:in `require_with_graceful_fail'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/utils/win_tz.rb:15:in `calculate'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll.rb:135:in `set_timezone'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll.rb:123:in `block in configuration'
        from <internal:kernel>:90:in `tap'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll.rb:122:in `configuration'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:44:in `configuration_from_options'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/commands/serve.rb:83:in `block (2 levels) in init_with_program'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `block in execute'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `each'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `execute'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary/program.rb:44:in `go'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary.rb:21:in `program'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/exe/jekyll:15:in `<top (required)>'
        from C:/Ruby32-x64/bin/jekyll:32:in `load'
        from C:/Ruby32-x64/bin/jekyll:32:in `<main>'
<internal:C:/Ruby32-x64/lib/ruby/3.2.0/rubygems/core_ext/kernel_require.rb>:38:in `require': cannot load such file -- tzinfo (LoadError)
        from <internal:C:/Ruby32-x64/lib/ruby/3.2.0/rubygems/core_ext/kernel_require.rb>:38:in `require'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/external.rb:57:in `block in require_with_graceful_fail'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/external.rb:55:in `each'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/external.rb:55:in `require_with_graceful_fail'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/utils/win_tz.rb:15:in `calculate'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll.rb:135:in `set_timezone'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll.rb:123:in `block in configuration'
        from <internal:kernel>:90:in `tap'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll.rb:122:in `configuration'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/command.rb:44:in `configuration_from_options'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/lib/jekyll/commands/serve.rb:83:in `block (2 levels) in init_with_program'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `block in execute'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `each'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `execute'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary/program.rb:44:in `go'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/mercenary-0.4.0/lib/mercenary.rb:21:in `program'
        from C:/Ruby32-x64/lib/ruby/gems/3.2.0/gems/jekyll-4.3.3/exe/jekyll:15:in `<top (required)>'
        from C:/Ruby32-x64/bin/jekyll:32:in `load'
        from C:/Ruby32-x64/bin/jekyll:32:in `<main>'
```
<br>
tzinfo 가 없어서 에러가 발생하였고 Gemfile에 다음 정보를 추가해서 해결

```
gem 'tzinfo'
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
```

## Github Action 빌드 에러
https://github.com/cotes2020/jekyll-theme-chirpy 테마를 통해서 github 테마를 만들었는데 로컬에서는 이슈없이 빌드하고 서버띄우는데 이슈는 없었음<br>
그런데 이상하게 github에 push하고 github actions 를 통해서 빌드하면 다음과 같은 에러가 계속 발생함

```
Configuration file: /home/runner/work/leesp2.github.io/leesp2.github.io/_config.yml
 Theme Config file: /home/runner/work/leesp2.github.io/leesp2.github.io/_config.yml
            Source: /home/runner/work/leesp2.github.io/leesp2.github.io
       Destination: /home/runner/work/leesp2.github.io/leesp2.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
Error: Can't find stylesheet to import.
  ╷
1 │ @import 'dist/bootstrap';
  │         ^^^^^^^^^^^^^^^^
  ╵
  main.bundle.scss 1:9                                                                         @import
  /home/runner/work/leesp2.github.io/leesp2.github.io/assets/css/jekyll-theme-chirpy.scss 1:9  root stylesheet 
  Conversion error: Jekyll::Converters::Scss encountered an error while converting 'assets/css/jekyll-theme-chirpy.scss':
                    Can't find stylesheet to import.
                    ------------------------------------------------
      Jekyll 4.3.3   Please append `--trace` to the `build` command 
                     for any additional information or backtrace. 
                    ------------------------------------------------
/home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-sass-converter-3.0.0/lib/jekyll/converters/scss.rb:175:in `rescue in convert': Can't find stylesheet to import. (Jekyll::Converters::Scss::SyntaxError)
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-sass-converter-3.0.0/lib/jekyll/converters/scss.rb:159:in `convert'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:105:in `block in convert'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `each'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `reduce'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:104:in `convert'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:84:in `render_document'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/renderer.rb:63:in `run'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:572:in `render_regenerated'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:564:in `block in render_pages'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:563:in `each'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:563:in `render_pages'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:211:in `render'
	from /home/runner/work/leesp2.github.io/leesp2.github.io/vendor/bundle/ruby/3.1.0/gems/jekyll-4.3.3/lib/jekyll/site.rb:80:in `process'
	...
```
<br>
처음에는 _sass/main.bundle.scss 파일에 있는 @import 'dist/bootstrap'; 를 아예 지워버리고 빌드를 돌려봤는데 잘 돌아가서 이슈가 해결됐구나 생각<br>
하지만 마크업이 뭔가 깨져서 페이지가 이상하게 보이는 현상이 발생함<br>
결국 찾다가 확인 Github Actions로 빌드 배포 하면서 jekyll.yml 파일이 .github/workflow/jekyll.yml 에 추가되는데 이때 다음과 같이 jekyll 환경변수 설정이 필요함


```
env:
    JEKYLL_ENV: production bundle exec jekyll b
```

## 모바일 페이지에서 side 메뉴 버튼, 검색 버튼이 반응이 없는 이슈
2024년 6월 2일 기준으로 https://github.com/cotes2020/jekyll-theme-chirpy 를 가지고 github를 만들었는데 해당 github를 보지 않고 다른 블로그들의 만드는 방법만 가지고 만들다 보니 이슈가 발생<br>
결론적으로 해당 이슈가 발생한 부분은 /assets/js/dist/ 폴더 및 하위 파일들이 존재해야 하는데 해당 파일들이 존재하지 않아 발생한 이슈였음
결국 전체적으로 다시 설치를 진행함