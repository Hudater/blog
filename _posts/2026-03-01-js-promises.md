---
## Hashnode
slug:
subtitle: Is GSoC just Promise.any()
domain: hashnode.hudater.dev

# Cover Image URL of the post
# String | Optional
# Note: You must upload the image to Hashnode's CDN, before you can use it here.
# Ex: https://cdn.hashnode.com/res/hashnode/image/upload/v1681132538878/itnaYF1h-.png
# - To upload, Login to Hashnode and go to https://hashnode.com/uploader
#   Use the URL that is generated after the upload.
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1768907490094/TEkoHSA4S.jpg?auto=format

# SEO Title
# String | Optional
# Ex: Top 4 React UI Libraries for 2023
# - This is equivalent to SEO TITLE option present in draft settings
#   of a post in Hashnode editor.
# - You can also update a post to update this later.
# seoTitle:

# SEO Description
# String | Optional
# Ex: A curated list of the best React UI libraries for 2023
# - This is equivalent to SEO DESCRIPTION option present in
#   draft settings of a post in Hashnode editor.
# - You can also update a post to update this later.
# seoDescription:

# Slug of the series that you want your post to be a part of
# String | Optional
# Ex: react-series
# - This is equivalent to "ADD TO A SERIES" option present in
#   draft settings of a post in Hashnode editor.
# - If invalid series is given, the post will not be added to any series.
# - You can update the post again to correct it later.
# - You can find series information from the series section in your publication dashboard.
#   You can also edit the series information from there.
# seriesSlug: // slug of the series

enableToc: true

# Save post as draft
# Boolean | Optional
# Default value: false // by default the post will be published.
# Ex: true
# - If true, the post will be saved as a draft.
# - You can also update a draft with all the above attributes.
# - This draft will be available under Drafts section of the
#   left sidebar in your publication dashboard.
# - Note: Once you remove this attribute, the post will be
#   published and removed from drafts automatically.
# - This follows the same rules as a post create and update
#   flow as well as the slug rules mentioned since
#   beginning of this manual.
saveAsDraft: false

## Jekyll
title: Is GSoC just Promise.any()
layout: post
date: 2026-03-01 05:30:00 +0530
categories: [chaicode, js-series]
comments: true
pin: false
tags:
  - js
  - promises
  - async
image:
  path: "https://res.cloudinary.com/djsasyvfl/image/upload/v1772367469/21b11c46-3d90-4716-9ec7-15bef8904d6d.png"
  alt: "Promises Flow in JS"
---

> GSoC season is approaching
>
> You have your READMEs all updated
>
> Let's make sure you are ready to be an "Open Source Contributor"

Let's understand what your OSS journey and JS Promises have in common.

## Promise

You are an avid browser of GitHub with contribution graph drier than Sahara.

You friend Harsh who started as "Black Hat Hacker" in 2018 to "Crypto Trader" in 2020 is your best Tech Bro

Harsh advices you a remedy for that GitHub. He says, "Yahi tarika hai bro FANG mein jane ka, senior bhaiya bhi aise hi gye the"

The advice is to contribute to a popular repo @[github](https://github.com/hudater/linkme){:target="\_blank"}

You realize the repo is by a 10x developer, you hesitate.

Harsh appears, excalims, "Be confident bro! Bas README mein typo fix kar. Start small. Maintainers notice consistency."

So you fork the repo, change images in README and open a PR. And you wait!

The state you are in is exactly the same as a Promise.

> In JavaScript, a Promise represents:
>
> > A value that will be available in the future.

In OSS terms:

Your PR has three possible states:

| State     | Description                |
| --------- | -------------------------- |
| Pending   | Maintainer hasn’t reviewed |
| Fulfilled | PR merged                  |
| Rejected  | PR closed                  |

The default state is pending. Once it’s merged or closed there’s no undo, i.e, **State is permanent**

## Promise Creation

```js
const firstPR = new Promise((resolve, reject) => {
  const merged = Math.random() > 0.5;
  if (merged) {
    resolve("LGTM 🎉");
  } else {
    reject("Get a life");
  }
});
```

> `(resolve, reject) => { ... }`
>
> this part is known as the "executor function"

The moment line 1 executes, two things happen:

1. Executor function runs immediately.
2. Promise is born in the Pending state.

The PR is open yet no response from maintainer but the process has begun

## State Decision

Inside the executor, only two functions matter:

- resolve(value)
- reject(reason)

Whichever gets called first decides the fate of the Promise.

Just like whichever button the maintainer clicks first decides your PR.

```js
resolve("LGTM 🎉"); // PR merged
reject("Changes requested ❌"); // PR closed
```

The moment one of the function runs, the state of your Promise changes:

| Function | State     |
| -------- | --------- |
| Resolve  | Fulfilled |
| Reject   | Rejected  |

If none of the functions are called, your Promise stays in the pending state just like your PR.

### Then

Let's say the maintainer sees an opportunity to save more famous repos from your "Contributions" and merges your PR.

You would be elated afterall you have become an "Open Source Contributor"

What you do after this change of state is handled by `.then()`

```js
firstPR.then((message) => {
  console.log("Tweeting screenshot:", message);
});
```

Upon calling `.then()` following happens:

- It attaches a fulfillment handler
- It runs when the Promise becomes Fulfilled
- **It returns a new Promise**

Since it returns a new Promise, we can be certain the old Promise `firstPR` is not touched but rather a new Promise is created based on `firstPR` outcome

**Whatever the previous `.then()` returns becomes the value for next Promise. This is called Promise Chaining**

```js
firstPR
  .then(() => "Time to write real feature")
  .then((nextStep) => {
    console.log(nextStep);
  });
```

#### Promise inside Then

> What if I return another Promise?
{: .prompt-tip }

You're learning! Let's say you do something like this

```js
firstPR
  .then(() => {
    return new Promise((resolve) => {
      setTimeout(() => resolve("Feature merged"), 1000);
    });
  })
  .then(console.log);
```

The second `.then()` **waits until the returned Promise resolves.**

It ensures control in the chain.
<br/>
Just like you don’t apply for GSoC until your contributions are real.

### Catch

We can handle a  PR but what about a rejection?

Let's say your beautiful README changes were deemed unworthy by that arrogant maintainer. We need to tweet about that too!

This is where we use `.catch()`

```js
firstPR
  .then(() => {
    throw new Error("Build failed");
  })
  .catch((err) => {
    console.log("Fixing:", err.message);
  });
```

`.catch()` only runs when Promise becomes `rejected.` Funnily enough, `.catch()` also returns a new Promise so the previous drill applies

### Throw inside Then

> What if I `throw` inside `.then()`?
{: .prompt-tip }

The whole chain becomes `rejected`

The error propagates down the chain.

It skips all subsequent `.then()` calls until it finds a `.catch()`.

Example:

```js
firstPR
  .then(() => {
    throw new Error("Build failed");
  })
  .then(() => {
    console.log("This will NOT run");
  })
  .catch((err) => {
    console.log("Caught:", err.message);
  });
```

Output:
```text
Caught: Build failed
```

> Why Does This Happen?
{: .prompt-tip }

Because under the hood `.then()`

is conceptually something like this:

```js
.then(successHandler, undefined)
```

If you `throw()`, JS automatically converts that into:

```js
return Promise.reject(error);
```

So throwing inside `.then()` is just a cleaner way of rejecting the next Promise in the chain.

### Finally

That was about tweets, we can be a bit casual on twitter but that won't do on LinkedIn.

HR needs to see that you take rejections on the chin and move forward with "New Learning, a New Chapter"

You need to frame your README PR as if that was the peak of your coding career.

**We will use `.finally()` when you want something to run regardless of the outcome**

```js
firstPR
  .then(() => {
    console.log("I Love Open Source");
  })
  .catch(() => {
    console.log("Maintainers are arrogant");
  })
  .finally(() => {
    console.log("My latest contribution taught me everything about life. Here are my insights!");
  });
```

`.finally()` returns nothing, it's just final cleanup crew to make sure everything was done.

> What if I `throw` inside `.finally()`?
{: .prompt-tip }

You have become too powerful for your own good.

Throwing inside `.finally()` overrides everything. The whole chain becomes `rejected`

## Static Methods

Till now you were a solo contributor working alone.

If we [recall from git blogs](https://blog.hudater.dev/categories/git-series/), we can understand that OSS contribution is not about a single contributor.

Let's work in a team (or at least pretend to). Now the contributors consist of you, Harsh and Akash. We will call this squad "ChaiWale"

### All

ChaiWale decide, "aaenge to sab sath mein varna koi nhi"

Let's say you do something like this:

```js
Promise.all([yourPR, harshPR, akashPR])
  .then((results) => {
    console.log("All merged:", results);
  })
  .catch((err) => {
    console.log("One failed:", err);
  });
```

Which results in:

- Resolve only if ALL promises fulfill
- Reject immediately even if ONE rejects

If all promises resolve, you get an array of results:

```text
["LGTM 🎉", "LGTM 🎉", "LGTM 🎉"]
```

The order is preserved even if Akash’s PR merged first,

### AllSettled

ChaiWale has matured, you say, "Jo hua so hua. Pehle dekhte hain kya hua"

```js
Promise.allSettled([yourPR, harshPR, akashPR])
  .then((results) => {
    console.log(results);
  });
```

`AllSettled()` does:

- Waits for ALL promises to settle
- Never rejects
- Returns structured results

Example output:

```text
[
  { status: "fulfilled", value: "LGTM 🎉" },
  { status: "fulfilled", value: "We don't like tech bros" },
  { status: "rejected", reason: "TM 🎉" }
]
```

### Race

ChaiWale are getting competetive, you say, "Jo pehle merge karega, uska LinkedIn post sab share karenge"

```js
Promise.race([yourPR, harshPR, akashPR])
  .then((winner) => {
    console.log("Hero of the day:", winner);
  })
  .catch((err) => {
    console.log("First response was rejection:", err);
  });
```

`Race()` does:

- Settles as soon as the **FIRST** promise settles.
- If first result is rejection, whole thing gets rejected.
- Doesn’t wait for others.

### Any

ChaiWale has not realized inner fighting doesn't result in any merged PRs. Afterall, one friend need to join somewhere to give others a referral.

You say, "Yaar koi ek to aage badho, sare nalle hi pade rhoge kya"

```js
Promise.any([yourPR, harshPR, akashPR])
  .then((winner) => {
    console.log("Squad survives because of:", winner);
  })
  .catch((error) => {
    console.log("Sab reject. Time to grind.");
  });
```

`Race()` does:

- **Resolves** when the **FIRST promise fulfills**
- Ignores rejections
- Rejects only if ALL reject
- Throws AggregateError if everyone fails

## Conclusion

Throughout your journey, you learned alot about Promises and Open Source.

ChaiWale is now a mature group of Devs who don't chase after merged PRs, rather meaningful contributions to projects they use and admire.

Maybe one day, ChaiWale will create something of their own and won’t be waiting for `resolve()`

:wq
