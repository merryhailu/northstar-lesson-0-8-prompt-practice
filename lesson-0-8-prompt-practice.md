## question: "We're considering segmenting our customer base into three tiers based on spending: high-value, mid-value, low-value. Can you tell me what threshold values would make sense for these tiers, and what we should do once we have them?"

## Part A: Apply the "Explain Like I'm New" pattern

# structured prompt

You are a patient teacher of data analytics concepts.

Explain customer segmentation by spending tier and threshold values for these tiers, and what we should do once we have them in plain language to someone who has just started learning analytics. Assume I know basic SQL but no statistics.

Use a real-world example involving a small business working on company called Northstar Data Group. Avoid jargon. If a technical term is necessary, define it inline.

Output: a 200-300 word explanation with one example.

## Claude Response

Northstar Data Group has just landed a small retail client — a local outdoor gear shop called Summit Supply. The shop has 800 customers in their database, and the owner wants to know: who are my best customers, and what should I do about it?
Your first task is to sort those 800 customers into spending tiers — groups based on how much each person spent in the last 12 months.
Here's a simple three-tier split that makes sense for Summit Supply:

High-value — spent $300 or more. About 15% of customers. These people buy jackets, tents, full kits.
Mid-value — spent $75–$299. About 45% of customers. They buy regularly but haven't gone all-in.
Low-value — spent under $75. About 40% of customers. One-time buyers, or someone who grabbed a water bottle on sale.

To set these thresholds, Northstar would pull the data, sort customers by total spend, and look for natural gaps in the numbers — points where spending clusters noticeably. There's no universal rule; the right cutoffs depend on what this specific shop actually sells.
What Summit Supply should do with each tier:

High-value — reward loyalty. Invite them to a members-only gear preview night.
Mid-value — encourage growth. Offer a "spend $50 more, get free shipping" promotion.
Low-value — test re-engagement. Send one win-back email with a small discount, then move on if they don't respond.

In SQL, you'd calculate each customer's annual total, then use a CASE WHEN statement — basically an if/then rule — to label each row with their tier. Clean, repeatable, and something Northstar can automate for every client going forward.

## chatgpt Response

Customer segmentation by spending tier is a way to group customers based on how much money they spend, so a business can treat different customers in different ways instead of treating everyone the same.

At Northstar Data Group, imagine they run a small online analytics training store selling courses. Over a few months, they track how much each customer spends in total. Then they create simple “tiers” (groups) using threshold values (cut-off points that decide which group someone belongs to).

For example, they might define:

Low spenders: $0–$100
Mid spenders: $101–$500
High spenders: $501+

These thresholds are not random rules from SQL—they are business decisions, often based on patterns in the data or simple common sense when starting out.

Once customers are grouped, Northstar can take action. Low spenders might receive discount coupons to encourage a second purchase. Mid spenders might get recommendations for slightly more advanced courses. High spenders could be offered premium bundles, early access to new courses, or personal support, because they are already very valuable customers.

For example, suppose one customer, Sam, has spent $320 total. Sam falls into the mid spender tier. Northstar might email Sam suggesting a “data visualization bundle” that is slightly more expensive than what he usually buys but still realistic for his spending level.

The main idea is simple: instead of guessing what each customer wants individually, you use spending ranges to make smart, consistent decisions. This helps the business improve sales and also gives customers offers that feel more relevant to them.

## Part B: Apply the "Act as a Senior Analyst" pattern

# structured prompt

You are a senior data analyst with 10 years of experience in Northstar data group Company. I'm working at LinenLane, junior analyst, with access to one year of customer transaction data.

A Boss asks: "We're considering segmenting our customer base into three tiers based on spending: high-value, mid-value, low-value. Can you tell me what threshold values would make sense for these tiers, and what we should do once we have them?" Walk me through how you would approach this problem. What questions would you ask first? What pitfalls would you watch for? What's a common mistake juniors make on this kind of task?

I'm not asking for the answer. I'm asking for the way of thinking.

Output: a structured walk-through, organized by step (1, 2, 3, ...). Brief, like an experienced colleague explaining over coffee.

# Claude Response

1. Clarify the goal before touching the data
   Ask your boss: what decision will these tiers drive? Marketing emails? Loyalty rewards? Sales team focus? The answer changes everything. Tiers built for an email campaign look different from tiers built to flag VIP customers for personal outreach. Don't define thresholds in a vacuum.
2. Understand what "spending" means at LinenLane
   Before you write a single query, ask: does spending mean revenue, or profit? Does it include returns? Gift card purchases? One big order or twelve small ones? At a linen retailer, a customer who spent $400 on a duvet once behaves very differently from one who spent $400 across eight visits. Same number, very different customer.
3. Look at the data distribution first
   Pull total spend per customer for the year and just look at it — a simple histogram or a sorted list. You'll likely find a small cluster of heavy spenders at the top, a big middle group, and a long tail of one-time buyers. Let the natural shape of your data suggest where the breaks should fall, rather than picking round numbers like $100/$500 arbitrarily.
4. Sanity-check your tier sizes
   After you set thresholds, check how many customers land in each bucket. If "high-value" captures 2% of customers or 60%, something's off. Aim for tiers that are meaningfully sized and actionable — you need enough people in each group to actually do something with them.
5. Watch for the one-year blind spot
   You only have one year of data. That means a customer who just joined in November looks low-value even if they're actually a strong buyer. Flag this to your boss — a newer customer's annual spend isn't comparable to someone who's been shopping since January.
6. The common junior mistake
   Picking thresholds first, then justifying them after. It feels confident, but it's backwards. Thresholds should come from the data and the business goal — not from a guess dressed up as analysis. Show your reasoning, not just your answer.
7. Connect tiers to actions before you present
   Don't walk in with just three buckets and numbers. For each tier, have a one-line recommendation ready — what should LinenLane do differently for each group? That's what turns a segmentation exercise into something your boss can act on Monday morning.

## Chatgpt Response

1. First clarify what “value” actually means

Before touching data, I’d ask:

Is “spending” total per year, per month, or lifetime value per customer?
Are we using gross revenue or net revenue (after refunds/discounts)?
Do we care about frequency too, or only total spend?

This matters because different definitions completely change the tiers.

2. Understand the business goal behind the tiers

I’d ask:

Are we trying to increase revenue, improve retention, or target marketing better?
Will these tiers be used for email campaigns, pricing strategy, or reporting?

Without this, you might build perfectly “clean” tiers that don’t help anyone.

3. Explore the data first (don’t jump to thresholds)

I’d look at:

Distribution of customer spending (are most people low spenders?)
Outliers (a few customers spending extremely high amounts)
Median vs average spend (they often tell very different stories)

A common mistake is assuming the data is evenly spread — it rarely is.

4. Think in “business-friendly breaks,” not statistical purity

Instead of fancy modeling, I’d look for natural cut points like:

A big gap between spending groups
Percentiles (like bottom 50%, next 40%, top 10%)
Or simple business intuition (e.g., “under $100 feels low”)

But I would not set thresholds without checking if they create meaningful group sizes.

5. Validate the tiers

After proposing thresholds, I’d check:

Do we end up with useful group sizes, or is everything in “low”?
Do high-value customers actually look important (repeat purchases, etc.)?

Bad segmentation often looks neat but produces useless groups.

6. Decide what actions each tier triggers

This is where many juniors stop too early.

I’d ask:

What will marketing actually do differently for each group?
Can we realistically act on 3 segments, or is that too many/too few?

If nothing changes behavior, segmentation is just labeling.

Common pitfalls juniors make
Picking thresholds before understanding the business question
Using averages without checking skew (a few big spenders distort everything)
Forcing equal-sized groups even when customer behavior is uneven
Forgetting that segmentation must lead to action, not just charts
Big mindset shift

Good segmentation isn’t “finding the right numbers.”
It’s “finding cuts in the data that help the business make better decisions.”

## Part C: Apply the "Generate Code for X" pattern

# structured Prompt

You are a senior data analyst writing production-quality Python.

Write a short Pandas script that assigns each customer to "high," "mid," or "low" based on percentile (top 20% high, middle 60% mid, bottom 20% low) from a DataFrame.

Context: I have a DataFrame called `customers` with columns `customer_id`, `total_spend_2025`. The DataFrame has roughly 5,000 rows. Pandas version 2.2.

Constraints: Using segment new column.

Output: only the code, with brief inline comments explaining each step. No surrounding prose.

## Claude

import pandas as pd

# Calculate percentile thresholds from total_spend_2025

low_thresh = customers["total_spend_2025"].quantile(0.20)
high_thresh = customers["total_spend_2025"].quantile(0.80)

# Assign tier labels based on spend percentile cutoffs

customers["segment"] = pd.cut(
customers["total_spend_2025"],
bins=[float("-inf"), low_thresh, high_thresh, float("inf")],
labels=["low", "mid", "high"],
right=True
)

# Verify tier distribution looks reasonable

print(customers["segment"].value_counts().sort_index())
print(customers[["customer_id", "total_spend_2025", "segment"]].head(10))

## Chatgpt Responses

import pandas as pd

# Calculate percentile thresholds for segmentation

low_cut = customers["total_spend_2025"].quantile(0.20) # bottom 20% cutoff
high_cut = customers["total_spend_2025"].quantile(0.80) # top 20% cutoff

# Assign segments based on spend thresholds

customers["segment"] = pd.cut(
customers["total_spend_2025"],
bins=[float("-inf"), low_cut, high_cut, float("inf")],
labels=["low", "mid", "high"]
)

# Display result

print(customers)

## From this, I figured out that the outputs are almost similar when the prompt is structured. Even though there are slight differences, ChatGPT makes it easier to understand than Claude. The get the code is almost the same; the difference is variable names.
