---
layout: post
title: "Part A) MRP"
date: 2026-09-29 12:00:00 +0900
categories: [일기]
tags: [blog, jekyll]
---

MRP(Makov Reward Process)에 대한 내용 정리

Stochatsic Process에 대한 기본적인 지식은 있다는 가정하에 내용을 정리하였습니다.
본교 "추계과정" 수업을 수강 후 MRP부터 정리하였습니다.

## MRP

### Motvation
강화학습은 MDP로 formulation된 문제를 해결하는 알고리즘입니다. 그들을 알기 위해서는 MRP에 대한 기본적인 이해가 필요합니다.
MRP는 말 그대로 Markov Chain에서 Reward(보상)을 추가한 문제입니다.

### Reward
보상은 말 그대로 우리가 어떤 상태에서 어떤 상태로 이동하면 얻는 리워드를 의미합니다.
단순하게 생각해서 애니팡을 예시로 들고 싶습니다.
애니팡에서 두 캐릭터의 자리를 바꾸게 되면 터지면서 점수가 올라가게 됩니다. 

이처럼 어떤 상태에서 어떤 행동이나, 특정 상태에 있게 되면 보상을 얻게 되는 것을 의미합니다.
즉, 에이전트는 누적 보상을 최대화하는 방향으로 학습을 이어나갑니다.

$R(s) = \mathbbE[r_{t}|S_{t} = s]$
