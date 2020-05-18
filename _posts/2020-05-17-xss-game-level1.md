---
date: 2020-05-17 10:21:06
layout: post
title: 'xss-game level1'
subtitle: 'xss-game'
description: 'xss-game 사이트의 문제 풀이'
image: https://raw.githubusercontent.com/ykdy3951/ykdy3951.github.io/master/_src/xss-game/1/image.png
optimized_image: https://raw.githubusercontent.com/ykdy3951/ykdy3951.github.io/master/_src/xss-game/1/image.png
category: Webhacking
tags:
  - Webhacking
  - javascript
  - XSS
author: ykdy3951
paginate: false
---

# Webhacking - Xss

> 필요한 지식 : html, javascript, python
> 문제 : [xss-game level1](http://xss-game.appspot.com/level1).

target과 target code를 보자

### target

![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/xss-game/1/1.png?raw=true 'target')

### target code

`level.py`

```python
page_header = """
<!doctype html>
<html>
  <head>
    <!-- Internal game scripts/styles, mostly boring stuff -->
    <script src="/static/game-frame.js"></script>
    <link rel="stylesheet" href="/static/game-frame-styles.css" />
  </head>

  <body id="level1">
    <img src="/static/logos/level1.png">
      <div>
"""

page_footer = """
    </div>
  </body>
</html>
"""

main_page_markup = """
<form action="" method="GET">
  <input id="query" name="query" value="Enter query here..."
    onfocus="this.value=''">
  <input id="button" type="submit" value="Search">
</form>
"""

class MainPage(webapp.RequestHandler):

  def render_string(self, s):
    self.response.out.write(s)

  def get(self):
    # Disable the reflected XSS filter for demonstration purposes
    self.response.headers.add_header("X-XSS-Protection", "0")

    if not self.request.get('query'):
      # Show main search page
      self.render_string(page_header + main_page_markup + page_footer)
    else:
      query = self.request.get('query', '[empty]')

      # Our search engine broke, we found no results :-(
      message = "Sorry, no results were found for <b>" + query + "</b>."
      message += " <a href='?'>Try again</a>."

      # Display the results page
      self.render_string(page_header + message + page_footer)

    return

application = webapp.WSGIApplication([ ('.*', MainPage), ], debug=False)
```

Target code를 보면 위와 같이 되있다는 것을 알게 되었고,

```python
message = "Sorry, no results were found for <b>" + query + "</b>."
message += " <a href='?'>Try again</a>."
```

나는 이 코드에 집중을 해보았다.
이 코드를 보니 입력 창에 `html tag`가 들어갈 수 있음을 알게 되었고 테스트로 `<h1>`태그를 넣어 보았다.

![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/xss-game/1/2.png?raw=true 'input1')
![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/xss-game/1/3.png?raw=true 'input1-result')

위의 사진으로 부터 태그가 잘 작동함을 알게 되었고,
`<script>` 를 이용하여 `alert()`를 보내어 javacript를 실행 시키면 풀린다.

![placeholder](https://github.com/ykdy3951/ykdy3951.github.io/blob/master/_src/xss-game/1/4.png?raw=true 'level1-clear!')
