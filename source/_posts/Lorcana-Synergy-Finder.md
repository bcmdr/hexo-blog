---
title: Building a Lorcana Synergy Finder with ChatGPT – A 30-Minute Mobile Case Study
categories:
  - Articles
tags:
  - Development
  - ChatGPT
  - Mobile Development
  - API Integration
date: 2025-02-13 12:00:00
---

Our objective was straightforward: build a simple web tool to search Disney Lorcana card synergies by scanning card **rules text** for multiple keywords (for example, **"draw item"**). Unlike traditional tools that filter by set or card type, this tool had to quickly identify potential card interactions based solely on their text. The key requirements were:

- **Search within card text**, not just card names.
- **Support multiple keywords**, like “draw” and “item.”
- **Display card images and details instantly.**
- **Ensure a mobile-friendly design.**

## The Methodology

### 1. Defining the Goal

I needed a flexible search tool that could handle text-based queries and deliver instant results. I specified the functionality clearly to ChatGPT by describing the desired interface and behavior in plain language.

### 2. Development Environment and Tools

I built the entire prototype in **30 minutes on my phone**, leveraging:
- **ChatGPT Models**:  
  - **o3-mini-high** was used for fast, straightforward code fixes.  
  - **GPT-4o** provided detailed explanations and handled more complex features like debouncing and API request cancellation.
- **Paist**:  
  This is my custom app that lets me paste code from ChatGPT. Paist saves the code to a Google Firebase database and generates a URL to load it in an iframe, enabling real-time testing on my phone.

### 3. The Process

#### Getting Started (Part 1)
- I described the idea to ChatGPT:  
  > "Build me a web page that uses the Lorcana card API to help me find synergies. Search by regular expression on what the card contains. For example, ‘draw item’ should return any card that contains both ‘draw’ and ‘item’."
- ChatGPT returned a basic working example that performed a keyword search using the Lorcast API endpoint.
- I copied the code into Paist, tested it on my phone, and confirmed that:
  - The search input triggered API requests.
  - Cards matching the query appeared with images.
  - Basic styling was applied.

This quick MVP proved the concept worked, even though it was rough around the edges.

#### Optimizing Search and Performance (Part 2)
- Testing revealed issues such as:
  - **Excessive API calls:** Every keystroke initiated a new request.
  - **Overlapping responses:** Rapid input changes caused outdated queries to interfere.
  - **Flickering and slow feedback:** The user experience was not smooth.
- I prompted ChatGPT to implement a 1-second debounce and to cancel any pending API request when a new one was initiated.
- ChatGPT’s solution integrated a debounce function and AbortController, resulting in a responsive search experience that only updated with the latest query.

#### Polishing the User Experience (Part 3)
- I then focused on improving the display and interactivity of the cards:
  - **Interactive Overlays:** Tapping a card reveals an overlay showing detailed card text and version information (if available).
  - **Mobile-Friendly Interactions:** I replaced hover-based actions with tap events to ensure smooth behavior on touch devices.
  - **Grid Layout Adjustments:** I ensured the cards were laid out in a responsive grid, always showing at least two cards per row on mobile.
  - **Single Overlay Policy:** Tapping one card hides overlays on all other cards to avoid clutter.
- These improvements were iterated upon with targeted ChatGPT requests, ensuring that the final product was both functional and polished on mobile.

## Key Lessons and Takeaways

- **Explain your problem in plain language** when working with ChatGPT.
- **Switch between models strategically:**  
  - **o3-mini-high** for quick fixes.
  - **GPT-4o** for handling complex logic.
- **Test frequently:** Using Paist allowed rapid testing and iteration on a mobile device.
- **Implement debouncing and request cancellation** to optimize live search performance.
- **Iterate quickly:** A working MVP, even if rough, is the best starting point for further improvements.

## Final Outcome

The final Lorcana Synergy Finder features:
- **Efficient, debounced search** with cancellation of outdated API requests.
- **A responsive grid layout** that clearly displays card images and details on mobile.
- **Interactive cards** that reveal detailed card text and version information on tap, with only one overlay visible at a time.
- A fully functional tool built entirely on my phone in just **30 minutes**—demonstrating the power of combining ChatGPT with rapid mobile prototyping via Paist.

This case study shows that with a clear goal, strategic use of ChatGPT models, and effective mobile testing tools, you can build high-quality software quickly—even on the go.

Happy coding!
