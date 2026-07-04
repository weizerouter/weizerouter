# Fair Use Policy

WeizeRouter implements **Unlimited Fair Use with Cooldown Protection** to ensure gateway stability and quality service for all users.

---

## Overview

Fair Use is designed to:
- Maintain gateway stability and uptime
- Ensure quality service for all active users
- Prevent gateway overload and provider rate limits
- Balance unlimited access with responsible usage

---

## How Fair Use Works

### Basic Principle
**Fair Use = Unlimited usage with automatic cooldown protection when needed**

WeizeRouter does NOT enforce hard token limits or request caps. Instead, the system monitors gateway health and applies temporary cooldowns only when necessary to maintain stability.

---

## Package Tiers and Fair Use

### Mini Trial & Trial Packages
**Fair Use Level:** Basic

- Suitable for testing and learning
- Cooldown may trigger during peak usage
- Ideal for small projects and experimentation

### Pro Package
**Fair Use Level:** Higher

- Suitable for daily development work
- Higher threshold before cooldown
- Better for regular usage patterns

### Ultimate Package
**Fair Use Level:** Unlimited

- **No hard limits on tokens or requests**
- Cooldown protection with fastest recovery
- Designed for power users and production workloads
- Highest priority during peak times

---

## Cooldown Protection

### What is Cooldown?

Cooldown is a temporary pause applied when:
- Gateway is experiencing high load across all users
- Specific model provider is rate-limited
- System detects unusual usage patterns that could affect stability

**Cooldown is NOT:**
- A punishment or penalty
- A hidden rate limit
- Applied arbitrarily

**Cooldown IS:**
- A protective measure for gateway stability
- Applied fairly based on real-time system health
- Temporary and automatically recovers

---

## Cooldown Recovery

**Recovery Time:**
- Mini Trial / Trial: Standard recovery time
- Pro: Faster recovery priority
- Ultimate: Fastest recovery with highest priority

**During Cooldown:**
- API returns HTTP 429 (Too Many Requests)
- Error message explains cooldown status
- User can check dashboard for recovery time estimate

**After Cooldown:**
- API access automatically restored
- No manual action required
- Full service resumes immediately

---

## Usage Best Practices

### Recommended Practices
1. **Implement retry logic** — Use exponential backoff for failed requests
2. **Cache responses** — Cache repeated queries to reduce load
3. **Batch requests** — Group similar requests when possible
4. **Monitor usage** — Check dashboard regularly for token consumption
5. **Use appropriate models** — Choose cost-effective models for your use case

### What to Avoid
1. **Excessive polling** — Don't poll APIs continuously without delays
2. **Unnecessary requests** — Cache results instead of re-requesting
3. **Stress testing** — Don't use production gateway for load testing
4. **Sharing API keys** — Each user should have their own key

---

## Real-world Usage Examples

### Example 1: Development Work (Pro Package)
**Daily Usage:** 500K tokens  
**Pattern:** Steady usage throughout the day  
**Cooldown Risk:** Low

**Why:** Steady usage allows gateway to distribute load efficiently.

---

### Example 2: AI Agent (Ultimate Package)
**Daily Usage:** 2M tokens  
**Pattern:** Burst usage during processing, then idle  
**Cooldown Risk:** Very Low

**Why:** Ultimate package has highest priority and fastest cooldown recovery.

---

### Example 3: Stress Testing (Any Package)
**Usage Pattern:** Sending 1000 requests per second  
**Cooldown Risk:** Very High

**Why:** This pattern overloads the gateway and triggers cooldown protection immediately.

---

## Fair Use vs. Hard Limits

**WeizeRouter Fair Use:**
- ✅ Unlimited tokens with cooldown protection
- ✅ Transparent system health monitoring
- ✅ Automatic recovery without manual action
- ✅ Real-time status in dashboard

**Traditional Hard Limits (Not used by WeizeRouter):**
- ❌ Fixed token caps (e.g., 100K tokens per day)
- ❌ Request rate limits (e.g., 10 req/min)
- ❌ Manual approval for additional quota
- ❌ Pay-per-token billing

---

## Monitoring Your Usage

**Dashboard Features:**
- Real-time token consumption tracking
- Usage history by model
- Cooldown status indicator
- Recovery time estimate

**Access Dashboard:**
- Website: [https://weizerouter.web.id/dashboard](https://weizerouter.web.id/dashboard)
- Telegram Bot: [@WeizeRouterBot](https://t.me/WeizeRouterBot) (usage stats command)

---

## Error Response During Cooldown

**HTTP 429 Response:**
```json
{
  "error": {
    "message": "Fair use cooldown active. Gateway is under high load. Please retry in a few moments.",
    "type": "rate_limit_error",
    "code": "fair_use_cooldown"
  }
}
```

**Recommended Handling:**
```python
import time
from openai import OpenAI

client = OpenAI(
    base_url="https://weizerouter.web.id/v1",
    api_key="your_api_key"
)

def call_api_with_retry(messages, max_retries=3):
    for attempt in range(max_retries):
        try:
            response = client.chat.completions.create(
                model="ag/gemini-3.5-flash-low",
                messages=messages
            )
            return response
        except Exception as e:
            if "429" in str(e) and attempt < max_retries - 1:
                wait_time = 2 ** attempt  # Exponential backoff
                print(f"Cooldown active, waiting {wait_time}s...")
                time.sleep(wait_time)
            else:
                raise e

# Usage
response = call_api_with_retry([
    {"role": "user", "content": "Hello!"}
])
```

---

## Frequently Asked Questions

**Q: What are the exact token limits?**  
A: WeizeRouter does NOT enforce hard token limits. Fair Use with cooldown protection is applied dynamically based on gateway health.

**Q: Will I be charged for requests during cooldown?**  
A: No. Requests during cooldown are rejected and NOT billed.

**Q: How do I avoid cooldown?**  
A: Follow usage best practices: implement retry logic, cache responses, avoid excessive polling, and use appropriate models.

**Q: Does Ultimate package have unlimited tokens?**  
A: Yes, Ultimate package provides unlimited fair use. Cooldown protection may still apply during extreme gateway load, but Ultimate users get highest priority and fastest recovery.

**Q: Can I upgrade my package to avoid cooldown?**  
A: Upgrading to Pro or Ultimate provides higher cooldown thresholds and faster recovery, but cooldown protection is a gateway-wide stability measure that may affect all users during peak load.

---

## Support

Questions about Fair Use?
- Telegram Bot: [@WeizeRouterBot](https://t.me/WeizeRouterBot)
- LinkedIn: [Wang Weize](https://www.linkedin.com/in/weize-wang-4262b7406)

---

**Last Updated:** July 2026
