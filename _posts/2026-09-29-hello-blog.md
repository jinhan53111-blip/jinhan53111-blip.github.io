---
layout: post
title: "Part A) MRP(Markov Reward Process)"
description: "Understanding Reinforcement Learning from the Foundations of Markov Reward Processes."
date: 2026-09-29 12:00:00 +0900
categories: [RL]
tags: [blog, jekyll]
---

MRP(Markov Reward Process)에 대한 내용 정리

Stochastic Process에 대한 기본적인 지식은 있다는 가정하에 내용을 정리하였습니다.  
본교 "추계과정" 수업을 수강 후 MRP부터 정리하였습니다.

---

## MRP

### Motivation

강화학습은 MDP로 formulation된 문제를 해결하는 알고리즘입니다.  
그들을 알기 위해서는 MRP에 대한 기본적인 이해가 필요합니다.

MRP는 말 그대로 Markov Chain에서 Reward(보상)을 추가한 문제입니다.

---

### Reward

보상은 말 그대로 우리가 어떤 상태에서 어떤 상태로 이동하면 얻는 리워드를 의미합니다.

단순하게 생각해서 애니팡을 예시로 들고 싶습니다.  
애니팡에서 두 캐릭터의 자리를 바꾸게 되면 터지면서 점수가 올라가게 됩니다.

이처럼 어떤 상태에서 어떤 행동이나, 특정 상태에 있게 되면 보상을 얻게 되는 것을 의미합니다.

즉, 에이전트는 누적 보상을 최대화하는 방향으로 학습을 이어나갑니다.

$$
R(s) = \mathbb{E}[r_t \mid S_t = s]
$$

> 즉, $R(s)$는 state $s$에 있을 때 얻을 수 있는 보상들의 기댓값입니다.

#### 왜 기댓값을 사용할까요?

예를 들어 설명해보겠습니다.

- 50% 확률로 +10을 얻고,
- 50% 확률로 -2를 얻는다고 가정하겠습니다.

그럼,

$$
R(s) = 0.5 \times 10 + 0.5 \times (-2) = 4
$$

즉, 기댓값을 사용하게 됩니다.

그러므로, 동일한 state라도 보상이 확률적으로 변할 수 있기 때문에 기댓값을 사용합니다.

---

### Cumulative Return

$G_t$는 보상들의 누적합을 의미합니다.

여기서 이 개념이 왜 나와야 할까요?

먼저, 간단한 예제로 설명해보겠습니다.

> Given I drink coke today, what is likely my consumption for upcoming 10 days?  
> (Pepsi is $1 and Coke is $1.5)

이러면 콜라를 마신 사람이 다음날 또 콜라를 마실 수 있고,  
또 다른 확률로 펩시를 마실 수도 있습니다.

펩시도 동일한 형태일 겁니다.

그렇다면 우리는 1 ~ 10일차까지 콜라, 펩시를 마신 것들의 각 일차별 보상들을 모두 다 더해서 누적 보상합을 내줍니다.

그래서 우리는 이를 $G_t$라고 정의하겠습니다.

> $G_t$는 $t$ 시점을 포함한 미래의 reward들의 누적합을 의미합니다.

예를 들어,

$$
\begin{aligned}
G_0 &= r_0 + r_1 + r_2 + \cdots + r_9 \\
G_1 &= r_1 + r_2 + r_3 + \cdots + r_9 \\
&\vdots \\
G_8 &= r_8 + r_9 \\
G_9 &= r_9
\end{aligned}
$$

이렇게 정의할 수 있겠습니다.

따라서 우리는 다음과 같이 정의할 수 있습니다.

$$
\mathbb{E}[G_0 \mid S_0 = c]
$$
