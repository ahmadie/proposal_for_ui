# Proposal: UI/Charting Solution for Python and JavaScript Interoperability

## Overview

This proposal outlines a solution to integrate Python-based trading strategies with JavaScript front-end charting libraries. The goal is to create an interoperable system that can handle both simple and advanced charting needs, leveraging technologies like Nautilus Trader, Redis, Node.js, and GraphQL.

---

## 1. Simple Charts

### Python Side

- **Strategy Development**: Use the **Nautilus Trader** library to develop trading strategies and process data.
- **Data Publishing**: Publish strategy outputs—such as backtesting results, plots, and entry/exit signals—to a **Redis cache**.
- **Rust Integration**: Apply the same decorator approach using procedural macros in the Rust section of Nautilus.

### JavaScript Side

- **Charting Library**: Utilize the **TradingView Lightweight** or **Advanced Chart** library to render charts.
- **Data Subscription**: The JavaScript client will receive data via **Node.js** and **GraphQL** by subscribing to Redis channels.

### Data Communication Mechanism

- **Python Decorators**:
  - Apply decorators to functions and variables to enable automatic data transmission to Redis.
  - Publish data to predefined Redis channels.
  - Interface with a predefined JavaScript client that handles dynamic data updates.
- **Decorator Integration**:
  - Incorporate decorators for basic indicators like EMA into the strategy SDK.
  - Enable chart triggering with simple flags in the code.



---

## 2. Advanced Charts

### Advanced Decorators

- **Dynamic Channel Creation**:
  - Allow creation of new Redis channels on-the-fly.
  - Publish data to these channels.
- **JavaScript Subscription**:
  - Modify JavaScript code to subscribe to new variables (similar to existing GitHub Python wrappers).

### Enhancements Needed

- **Control Over API Calls**:
  - Gain finer control over front-end API calls.
- **Hot-Reloading/File Watching**:
  - Implement continuous hot-reloading to reflect real-time changes.

### Implementation Steps

1. **Node.js Server with Hot-Reloading**:
   - Develop a Node.js server that subscribes to Redis channels with hot-reloading enabled.
2. **GraphQL Backend Service**:
   - Implement a GraphQL server that interfaces with Redis.

### Potential Issues

- **Complexity and Risks**:
  - Modifying JavaScript code from Python and triggering hot-reloads can be complex and risky.
- **Proposed Solution**:
  - Instead of Python modifying JavaScript code, design the front end to handle dynamic data updates without code modifications.

---

## 3. Complex Charting Features

### Customized Data Handling

- **Manual Publishing and Subscribing**:
  - Strategy developers manage data publishing in Python and subscribing in JavaScript for advanced features.

---

## Next Steps

1. **Implement Backend Service**:
   - Develop the Node.js server with a GraphQL API to bridge Redis and the front end.
2. **Create a Prototype**:
   - Build a small prototype to test:
     - Python modifying JavaScript code.
     - Triggering hot-reloads.
     - Front-end handling of dynamic data updates.
