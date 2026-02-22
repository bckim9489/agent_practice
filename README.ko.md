<p align="right">
  🇰🇷 Korean | <a href="./README.md">🇺🇸 English</a>
</p>

# Agent Architecture Practice Lab

LLM 기반 Agent Architecture의 진화 과정을 실습으로 검증한 저장소입니다.\
ReAct 중심의 1세대 Agent부터, Workflow-Orchestrated 구조의 Post-ReAct
시스템까지 단계적으로 비교합니다.

------------------------------------------------------------------------

# Common Setup

실습 전반에서 사용하는 공통 실행 환경과 도구를 초기화하는 단계.

## 0. TEST

-   LLM 호출 및 API Key 정상 동작 확인
-   이후 실험을 위한 베이스라인 검증

## 1. Tools

-   Tavily Search 등 외부 Tool 정의
-   LangChain Tool 인터페이스 연결
-   Agent가 사용할 Action Layer 준비

------------------------------------------------------------------------

# \[Gen 1\] Prompt-driven Tool-Using Agents (ReAct-based Agents)

LLM이 스스로 Reason → Act → Observe 루프를 수행하는 1세대 Agent 패턴을
실험.

## 1. Zero-Shot ReAct

-   가장 순수한 ReAct 형태
-   계획 없이 즉시 추론 수행
-   Workflow 제어권이 전적으로 LLM에 있음

## 2. Conversational ReAct

-   대화 히스토리 기반 ReAct
-   Memory 추가 시 동작 변화 관찰
-   Stateless → Context-aware 전환 확인

## 3. Search-augmented ReAct (Self-Ask with Search)

-   질문을 하위 질문으로 분해(Self-Ask)
-   검색 Tool을 활용한 정보 탐색형 Agent 실험

## 4. ReAct Docstore

-   문서 저장소 기반 QA 수행
-   Retrieval이 추가되어도 제어는 여전히 LLM 중심임을 확인

------------------------------------------------------------------------

# \[Gen 2\] LLM Orchestrated Systems (Post-ReAct Agents)

LLM이 전체 흐름을 결정하던 구조에서 벗어나, 시스템이 실행을 설계하고
LLM은 구성 요소로 동작하는 2세대 패턴.

## 1. Plan-Then-Execute (Two-Phase Execution Architecture)

-   Planning 단계와 Execution 단계를 분리
-   즉흥적 ReAct의 한계를 구조적으로 개선

## 2. State Machine (FSM-based Orchestration)

-   명시적인 상태(State) 정의
-   상태 전이를 기반으로 실행 흐름 제어

## 3. Graph Execution (DAG Workflow Engine)

-   DAG 기반 실행 구조 도입
-   비선형 Workflow 및 노드 재사용 가능성 검증

## 4. DAG-Orchestrated Stateful Execution (FSM + Graph)

-   FSM 상태 관리 + DAG 실행 모델 결합
-   실제 서비스형 오케스트레이션과 유사한 구조 실험

## 5. Role-Specialized Multi-Agent System

-   Planner / Researcher / Builder / Critic / Supervisor 역할 분리
-   협업형 Multi-Agent 시스템 구현

## 6. Deterministic Guardrail

-   Validator / Guardrail을 통한 결과 검증
-   LLM 결과를 시스템 레벨에서 통제하는 방식 실험

------------------------------------------------------------------------

## Summary

Gen1: LLM이 스스로 모든 것을 판단하는 구조 (LLM-driven)

Gen2: 시스템이 Workflow를 설계하고 LLM은 역할로 참여 (System-driven)

이 실습은 단순한 Agent 사용법이 아니라, LLM Agent 설계가 Prompt
Engineering에서 Software Architecture 문제로 이동하는 과정을 보여줍니다.
