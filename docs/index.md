---
title: "R을 사용한 비구획분석"
author: "배균섭, 한성필, 윤석규, 조용순"
description: "이 책은 R 패키지를 사용하여 비구획분석을 쉽게 따라할 수 있도록 쓰여졌습니다.  값비싼 상용소프트웨어와 동일한 결과를 얻으면서, 한번 익혀두면 속도와 연속성 측면에서 잇점이 많은 것을 발견할 수 있을 것입니다.  무엇보다 무료로 사용할 수 있는 R기반의 공개 소프트웨어라는 점에서 많은 연구자 혹은 기관에서 손쉽게 설치하고 실행할 수 있으리라 생각됩니다."
date: "2017-10-20"
documentclass: "krantz"
knit: "bookdown::render_book"
site: bookdown::bookdown_site
#csl: springer-vancouver.csl
###
bibliography: ["assets/bib/manual.bib", "assets/bib/packages.bib"]
biblio-style: apalike
link-citations: yes
colorlinks: yes
lot: yes
lof: yes
fontsize: 12pt
monofont: "Source Code Pro"
monofontoptions: "Scale=0.7"
###
url: 'https\://asancpt.github.io/book-ncar/'
github-repo: asancpt/book-ncar
cover-image: assets/cover.jpg
output:
  bookdown::gitbook:
    css: css/style.css
    split_by: chapter
    config:
      toc:
        collapse: section
        before: |
          <li><a href="./index.html">R을 사용한 비구획분석</a></li>
        after: |
          <li><a href="http://github.com/asancpt/book-ncar">book-ncar Github 저장소</a></li>
#    download: [pdf, epub, mobi]
      edit:
        link: https://github.com/asancpt/book-ncar/edit/master/%s
        text: "Edit"
  bookdown::pdf_book:
    includes:
      in_header: latex/preamble.tex
    keep_tex: yes
    latex_engine: xelatex
    citation_package: natbib
---



# 책 머리에 {-}

[<img src="assets/cover.jpg" style="max-width:20%;min-width:80px;float:right;margin: 10px 10px 5px 5px" alt="Github repo" />](https://github.com/asancpt/book-ncar)

> 단순함은 궁극의 정교함이다.  
> Simplicity is the ultimate sophistication.  
> - 레오나르도 다빈치

이 책은 R을 사용하여 비구획분석을 간단히 수행할 수 있도록 안내할 것입니다. 
널리 쓰이지만 값비싼 상용 소프트웨어와 동일한 결과를 얻을 수 있음을 반복적으로 확인하였습니다. 
숫자 계산 뿐만 아니라 시각화도 가능하여 농도-시간 곡선, 용량군 별 파라메터의 forest plot 등의 유용한 그림도 쉽게 그릴 수 있습니다.
CDISC SDTM 표준을 따르는 용어를 사용한 것도 큰 장점입니다.

한번 익혀두면 속도와 연속성 측면에서 커다란 잇점이 있음을 것을 발견할 수 있을 것입니다. 
또한 재현가능한 연구를 보다 수월하게 구현할 수 있습니다.
무엇보다 무료로 사용할 수 있는 R기반의 공개 소프트웨어라는 점에서 학교, 연구소, 정부기관, 제약회사 등에서 라이센스 등의 제약 없이 손쉽게 설치하고 실행할 수 있으리라 생각됩니다.
책에 대한 피드백, 오탈자 신고 등은 [깃허브 저장소](https://github.com/asancpt/book-ncar/issues)에 남겨주십시오.

감사합니다.

2017년 10월  
서울아산병원 임상약리학과, 울산대학교 임상약리학교실  
교수 배균섭,  
전공의 한성필, 윤석규, 조용순

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="크리에이티브 커먼즈 라이선스" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />이 저작물은 <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">크리에이티브 커먼즈 저작자표시-비영리-동일조건변경허락 4.0 국제 라이선스</a>에 따라 이용할 수 있습니다.

<!-- https://creativecommons.org/choose/?lang=ko -->

## 감사의 글 {-}

본 출판물은 2016, 2017년도 정부(미래창조과학부)의 재원으로 한국연구재단 첨단 사이언스·교육 허브 개발 사업의 지원을 받아 수행된 연구입니다 (NRF-2016-936606).

## 저자 소개 {-}

**배균섭**

서울아산병원 임상약리학과 과장, 울산대학교 의과대학 임상약리학교실 교수입니다. 수십편의 논문을 저술하였고 20년 이상의 프로그래밍 경력을 갖고 있습니다.

**한성필**

서울아산병원 임상약리학과 전공의입니다.

**윤석규**

서울아산병원 임상약리학과 전공의입니다.

**조용순**

서울아산병원 임상약리학과 전공의입니다.