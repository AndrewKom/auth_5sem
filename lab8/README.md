---
title: "Лабораторная работа 8"
format: html
editor: visual
---

## Цель работы

1.  Развить практические навыки использования современного стека инструментов для генерации статических сайтов
2.  Освоить базовые подходы создания сайта на github и работа с GitHub Actions

## Исходные данные

1.  Github
2.  RStudio

## План

1.  Использовать репрозиторий из практической работы 7
2.  Поключить GitHub Actions
3.  Оформить отчет

## Описание шагов:

1.  Созданный сайт:\
    https://andrewkom.github.io/AUT_SSG/
2.  Настраиваем .github/workflows/quarto_publish.yml

```{=html}
<!-- -->
```
    on:
      push:
        branches: main

    name: Render and Publish

    jobs:
      build-deploy:
        runs-on: ubuntu-latest
        steps:
          - name: Check out repository
            uses: actions/checkout@v3
            
          - name: Set up Quarto
            uses: quarto-dev/quarto-actions/setup@v2
            with:
              # To install LaTeX to build PDF book 
              tinytex: true 
              # uncomment below and fill to pin a version
              # version: SPECIFIC-QUARTO-VERSION-HERE
          
          # add software dependencies here

          # To publish to Netlify, RStudio Connect, or GitHub Pages, uncomment
          # the appropriate block below
          
          # - name: Publish to Netlify (and render)
          #   uses: quarto-dev/quarto-actions/publish@v2
          #   with:
          #     target: netlify
          #     NETLIFY_AUTH_TOKEN: ${{ secrets.NETLIFY_AUTH_TOKEN }}
            
          # - name: Publish to RStudio Connect (and render)
          #   uses: quarto-dev/quarto-actions/publish@v2
          #   with:
          #     target: connect
          #     CONNECT_SERVER: enter-the-server-url-here
          #     CONNECT_API_KEY: ${{ secrets.CONNECT_API_KEY }} 

          - name: Publish to GitHub Pages (and render)
            uses: quarto-dev/quarto-actions/publish@v2
            with:
              target: gh-pages
            env:
               GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} # this secret is always available for github actions

3.  Локально запускаем quarto publish gh-pages

## Оценка результатов

Задача решена с помощью github. Я получил практические навыки использования современного стека инструментов для генерации статических сайтов.

## Вывод

В данной работе к существующему сайту был подключен функционал GitHub Actions.
