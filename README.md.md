
# LoanIQ — AI Loan Advisor  --- README

Demo Project |  AI + Fintech |  Loan Recommendation System
## 1. System Architecture

-   **Frontend**: Single-page HTML app (chat UI, EMI calculator, profile
    form)
-   **Backend (LLM Wrapper API)**: Handles prompt requests and returns
    AI responses
-   **State Management**: Browser `sessionStorage` (user session, chat,
    profile)
-   **Auth**: Mock authentication (token-based, stored in session)
-   **Core Modules**:
    -   Eligibility Engine (rule-based)
    -   EMI Calculator
    -   Product Recommendation Engine
    -   Chat + AI Integration

Flow: User Input → Profile/Chat → Context Builder → LLM API → Response →
UI Render

------------------------------------------------------------------------

## 2. Prompt Strategy

-   **System Prompt** defines:
    -   Role: AI Loan Advisor (India-specific)
    -   Product catalog constraints
    -   EMI formula
    -   Output format rules (concise, structured)
-   **Context Injection**:
    -   User profile (loan, income, credit score, etc.)
    -   Eligibility engine results
    -   Last 5--6 chat messages
-   **Guardrails**:
    -   No hallucinated products/rates
    -   Must include EMI, total repayment, interest
    -   Must include disclaimer (no guaranteed approval)

------------------------------------------------------------------------

## 3. Assumptions

-   Credit score is user-provided (not verified)
-   Interest rate uses **minimum rate** for estimates
-   FOIR threshold \~55% for risk flag
-   No real bank integration (mock product catalog)
-   API token is valid and reachable
-   EMI formula assumes fixed rate (no reducing rate changes)

------------------------------------------------------------------------

## 4. Test Cases

### Functional

1.  Valid login → user session created
2.  Invalid login → error shown
3.  Profile submission → recommendations displayed
4.  EMI calculation correctness
5.  Eligibility filtering based on:
    -   Credit score
    -   Income
    -   FOIR
6.  Chat query → AI response generated
7.  Language switch (EN ↔ HI)
8.  Voice input → text populated

### Edge Cases

1.  Zero interest (BNPL) EMI calculation
2.  Extremely high loan amount → ineligible
3.  Low credit score → rejection reasons shown
4.  Empty chat input → ignored
5.  API failure → error message displayed

### UI/UX

1.  Chat scroll behavior
2.  Typing indicator visibility
3.  PDF summary generation
4.  Session persistence after refresh

------------------------------------------------------------------------

## 5. How to Run

1.  Open `index_with_auth.html` in browser
2.  Login:
    -   demo@loaniq.ai / demo123
3.  Fill profile → click "Get AI Recommendations"
4.  Interact via chat or voice

------------------------------------------------------------------------

## 6. Notes

-   This is a **demo system**
-   Not a real lending platform
-   All outputs are **indicative only**
