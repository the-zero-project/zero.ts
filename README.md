<div align="center">
  <h1>🚀 zero.ts</h1>
  <h4>The Future of Full-Stack Development</h4>
</div>

<div align="center">
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Deno-000000?style=for-the-badge&logo=deno&logoColor=white" />
  <img src="https://img.shields.io/badge/zero.ts-FF6C37?style=for-the-badge&logo=database&logoColor=white" />
  <img src="https://img.shields.io/badge/Zero_Build-00D084?style=for-the-badge&logo=rocket&logoColor=white" />
</div>

<p align="center">
  <strong>Full end-to-end instant sync. UI to DB. Limited only by the speed of light. 🌟</strong>
</p>

<p align="center">
  <a href="#-remember-when-making-software-was-fun">Why <span style="font-weight: bold;">zero</span>?</a> •
  <a href="#-who-is-this-for">Who is this for?</a> •
  <a href="#-quickstart-zero-build-steps">Quickstart</a> •
  <a href="#-mind-blowing-features">Features</a> •
  <a href="#-examples">Examples</a> •
  <a href="#-events--views-real-time-reactivity-without-the-complexity">Events & Views</a> •
  <a href="#-locality-of-behavior-the-philosophy-that-changes-everything">Locality of Behavior</a> •
  <a href="#-why-we-built-this">Our Story</a>
</p>

---

## 🌟 Remember When Making Software Was Fun?

Before the build tools. Before the state management libraries. Before you needed a PhD in distributed systems just to toggle a checkbox. 😤

**zero brings back the joy.** Write your full-stack app like it's a single program. Because it is. 🎉

We were tired of it too. After years of GraphQL schemas, REST boilerplate, and state management nightmares, we finally cracked. Many sleepless nights going around in circles thinking "there MUST be a better way!" led us to build our own custom database and UI sync engine from scratch. Yes, we're that crazy. 😅

## 🎯 Who is this for?

**zero.ts is the weapon of choice for builders who ship.** If you're racing to validate your next product idea, building the SaaS that disrupts your industry, or watching your backlog grow faster than you can ship - **this is your unfair advantage**. Perfect for production SaaS apps, real-time collaboration platforms, B2B software, marketplace platforms, fintech products, and any product where shipping beats endless architecture meetings. We're honest: if you're building the next Facebook, you'll eventually outgrow us. But if you're building SaaS that serves thousands of customers, revolutionizes a workflow, or turns your domain expertise into a product - **zero.ts will get you there faster than anything else**. And here's the thing: if you do outgrow us? That means you're probably counting your revenue in millions and hiring your 50th engineer. At that point, you can afford to rebuild. Until then, ship features, not infrastructure. This is for developers who measure success in shipped features, not architectural diagrams. 🚀

### 💡 The Game-Changing Innovation

```tsx
// It may not look like one, but this is a COMPLETE full-stack todo app.
// No API routes. No state management. No build step. No database queries.
// Just async components with implicit full-stack type safety! 🤯

export async function TodoApp() {
  // Get ALL todos directly from the database. In your component. WHAT?! 🤯
  const todos = app.utils.values(app.db.todos);

  return (
    <div>
      <h1>✨ Magic Todo App ({todos.length} total)</h1>
      <TodoList todos={todos} />
    </div>
  );
}

export async function TodoList({ todos }: { todos: Todo[] }) {
  return (
    <div>
      <div style={{ marginBottom: "1rem" }}>
        <input
          id="new-todo"
          type="text"
          placeholder="What needs to be done?"
          style={{ marginRight: "0.5rem" }}
        />
        <button
          onClick={async () => {
            // Get the input value from DOM - client side! 🎭
            const input = document.getElementById("new-todo");
            const text = input.value.trim();

            if (!text) return;

            const result = await server(() => {
              // We're on the server now - text from client DOM just works! 🪄
              const todoId = crypto.randomUUID();
              const newTodo = {
                id: todoId,
                text, // <-- client variable used directly on server!
                done: false,
                createdAt: new Date(),
                sessionId: globalThis.sessionId, // current session
              };

              // Write to database!
              app.db.todos[todoId] = newTodo;

              // Return data from server - fully typed! 🎯
              return {
                success: true,
                todoCount: app.utils.values(app.db.todos).length,
                message: `Todo "${text}" added! You're crushing it! 💪`,
                todo: newTodo,
              };
            });

            // Clear the input and celebrate! 🎉
            input.value = "";

            // Optional: Show success (the UI already updated instantly!)
            console.log(result.message);
          }}
        >
          Add Todo ➕
        </button>
      </div>

      <ul>
        {todos.map((todo) => (
          <TodoItem todo={todo} />
        ))}
      </ul>
    </div>
  );
}

export async function TodoItem({ todo }: { todo: Todo }) {
  return (
    <li>
      <input
        type="checkbox"
        checked={todo.done}
        onChange={async () => {
          // This runs on the server. But you'd never know it. 🪄
          await server(() => {
            // Direct mutation on the database. Type-safe from DB to UI!
            todo.done = !todo.done; // That's it. You're done. 🤯
          });
        }}
      />
      <span>{todo.text}</span>
    </li>
  );
}
```

**Look at that beauty.** One line to toggle a todo. No actions. No reducers. No API calls. No loading states. Just `todo.done = !todo.done`.

This is what we've been waiting for. 🙌

## 🎯 Built for Startups Who Ship, Not Configure

**Your competitors are still arguing about state management. You're already profitable.** 💰

- **Instant everything**: Full-stack reactivity limited only by network latency ⚡
- **Zero build steps**: Just run `deno run` - no webpack, no babel, no bundlers 🎉
- **Implicit type safety**: From database to UI, TypeScript just works 🔒
- **No API layer**: Your frontend talks directly to your database (securely!) 🚀
- **Client state magic**: Use client variables in server functions. It just works™ 🪄
- **No GraphQL schemas**: No resolvers, no schema stitching, no N+1 nightmares 🙅
- **No REST boilerplate**: No more overfetching, underfetching, or version hell 🚫
- **Just TypeScript**: No learning 100 frameworks. Pure, beautiful TypeScript 💙

## ⚡ Quickstart: Zero Build Steps

```bash
# Clone and run. That's it. Seriously. 😎
git clone https://github.com/the-zero-project/zero.ts.git
cd zero.ts
deno run --allow-env --allow-net --allow-read --allow-write --allow-ffi ./src/main-vdom.ts

# Your full-stack app is live at http://localhost:8000 🎉
# No npm install. No build. Just run.
```

## 🎭 Mind-Blowing Features

### 🤏 The Network Layer You Don't Need to Think About

Your UI receives surgical binary DOM mutations, not bloated HTML strings. When you change one character in a 10,000 item list, that's exactly what gets sent over the wire - one tiny instruction. If we need to update large chunks, we intelligently switch to innerHTML. It's like having a senior performance engineer optimizing every update. 🎨

**8KB client runtime.** That's it. React alone is 42-46KB. Our entire custom binary protocol and sync engine fits in 8KB. Your users will think your app is installed locally. ⚡

### 🔮 True Full-Stack Components

Your components are **async by default**. Access anything, anywhere:

```tsx
export async function Dashboard({ userId }: { userId: string }) {
  // No hooks. No effects. No dependency arrays. Just write normal code! 🤩
  // Remember this nightmare? 😱
  // useEffect(() => { fetchUser() }, [userId])
  // useEffect(() => { fetchStats() }, [userId, user])
  // useEffect(() => { /* wait, why is this running twice? */ }, [])

  const user = app.db.users[userId];
  const stats = app.db.analytics.getUserStats(userId);

  // Reactive caching with automatic UI updates! 🔥
  const weather = app.db.weather[user.city];

  if (!weather) {
    // Fire and forget, the UI will update when the database does!
    fetch(`https://api.weather.com/${user.city}`).then(
      async (r) => (app.db.weather[user.city] = await r.json())
    );
  }

  return (
    <div>
      <h1>Welcome back, {user.name}! 👋</h1>
      {weather ? (
        <p>
          It's {weather.temp}° in {user.city} ☀️
        </p>
      ) : (
        <p>Loading weather... ⏳</p> // This will auto-update when DB updates!
      )}
      <p>You've completed {stats.completedTasks} tasks this week! 🎯</p>
    </div>
  );
}
```

> 🧠 **Smart Data Transfer**: Notice how we're accessing the entire `user` object but only rendering `user.name` and `user.city`? zero.ts automatically sends only `{ name, city }` to the client - not the entire user record with passwords, emails, or other sensitive data. Want to display the email too? Just add it to your JSX and it's automatically included. No more extending REST APIs or updating GraphQL queries. The same intelligence applies to event handlers - only the minimal data required for your client-side operations is transferred. Everything you need is at your fingertips, and the system figures out the rest. 🎯

### 🪄 Client State → Server Magic

Use DOM values in server functions. No serialization. No configuration. Just pure magic:

```tsx
export async function ContactForm() {
  return (
    <form>
      <input id="email" type="email" placeholder="your@email.com" />
      <textarea id="message" placeholder="How can we help?" />

      <button
        onClick={async (e) => {
          e.preventDefault();

          // Get values from DOM in the CLIENT portion 🎭
          const email = document.getElementById("email").value;
          const message = document.getElementById("message").value;

          // Use them in the SERVER portion - THIS IS REAL MAGIC! 🪄✨
          const result = await server(() => {
            // We're on the server now, but email and message just work!
            // NO BUILD STEPS. NO SERIALIZATION. IT JUST WORKS. 🤯

            // Save to database
            app.db.inquiries[crypto.randomUUID()] = {
              email, // <-- client variable used on server!
              message, // <-- another one!
              timestamp: new Date(),
              status: "new",
            };

            // Send email notification
            app.services.email.send({
              to: "team@startup.com",
              subject: `New inquiry from ${email}`,
              body: message,
            });

            return {
              success: true,
              inquiryCount: app.utils.values(app.db.inquiries).length,
            };
          });

          // Back on the client now, clear form and show success
          document.getElementById("email").value = "";
          document.getElementById("message").value = "";
          alert(`Thanks! This is inquiry #${result.inquiryCount}`);
        }}
      >
        Send Message 📨
      </button>
    </form>
  );
}
```

**Did you see that?** 👆 Client DOM values used directly in server code. No API. No serialization. It's revolutionary. 🚀

### 🚄 Instant Full-Stack Sync

Every change is instant. Every update is reactive. Every type is safe:

```tsx
// Provider pattern for clean data flow 📦
export async function DocumentProvider({ docId }: { docId: string }) {
  const doc = app.db.documents[docId];
  return <CollaborativeEditor doc={doc} />;
}

// The actual editor - receives doc as a prop and mutates it directly! 💥
export async function CollaborativeEditor({ doc }: { doc: Document }) {
  return (
    <div>
      <h2>{doc.title}</h2>
      <textarea
        value={doc.content}
        onChange={async (e) => {
          const newContent = e.target.value;
          await server(() => {
            // Just mutate the doc prop directly! 🤯
            // All connected users see updates instantly!
            doc.content = newContent;
            doc.lastEditedBy = sessionId;
            doc.lastEditedAt = new Date();
          });
        }}
      />
      <p>
        Last edited by {doc.lastEditedBy} at {doc.lastEditedAt} ✏️
      </p>
    </div>
  );
}
```

### 🔐 Session Magic

Easy session isolation with views - each user in their own universe:

```tsx
export async function TodoApp({ sessionId }: { sessionId: string }) {
  // Manual filtering - simple and explicit 🎯
  const todos = app.utils
    .values(app.db.todos)
    .filter((t) => t.sessionId === sessionId);

  // Or use views for reactive filtered collections! 🚀
  const myTodos = app.utils.view({
    path: "todos.*",
    predicate: (todo) => todo.sessionId === sessionId,
  });

  return (
    <div>
      <h1>My Todos ({myTodos.size}) 📝</h1>
      <TodoList todos={myTodos.array} />
    </div>
  );
}
```

## 📚 Examples That Make You Go "No Way!" 🤯

### 🤔 What You're NOT Writing

Before we show you what you ARE writing, let's appreciate what you're NOT:

```typescript
// ❌ NO GraphQL schema definitions
type Mutation {
  addToCart(productId: ID!): CartResponse!
}

// ❌ NO resolver implementations
const resolvers = {
  Mutation: {
    addToCart: async (_, { productId }, context) => {
      // auth checks, validation, DB queries...
    }
  }
}

// ❌ NO REST endpoint boilerplate
app.post('/api/cart/:productId', authenticate, validate, async (req, res) => {
  // CORS, body parsing, error handling...
});

// ❌ NO client-side state management
const [cart, setCart] = useState([]);
const [loading, setLoading] = useState(false);
const { mutate } = useMutation(ADD_TO_CART);

// ❌ NO useEffect dependency hell
useEffect(() => {
  // Why is this running 3 times? 😭
  fetchCart();
}, [user.id]); // <-- forgot user.cart.length, now stale data!

// ❌ NO re-render storms
const memoizedCart = useMemo(() => cart, [cart, user, /* ...17 more deps */]);
```

Forget all that. Here's what you actually write:

### 🛍️ E-Commerce in Minutes

```tsx
export async function ProductCard({ product }: { product: Product }) {
  const inCart = app.db.sessions[sessionId].cart?.includes(product.id);

  return (
    <div className="product-card">
      <img src={product.image} alt={product.name} />
      <h3>{product.name}</h3>
      <p>${product.price}</p>
      <button
        onClick={async () => {
          const result = await server(() => {
            // All this runs on the server, with full type safety! 🎯
            const session = app.db.sessions[sessionId];

            // Initialize cart if needed
            if (!session.cart) session.cart = [];

            // Add to cart
            session.cart.push(product.id);

            // Update inventory
            app.db.products[product.id].stock--;

            // Send email (why not? it's all server-side!) 📧
            app.services.email.send({
              to: session.email,
              subject: "Added to cart! 🛒",
              body: `${product.name} is waiting for you!`,
            });

            // Return typed response
            return {
              success: true,
              cartSize: session.cart.length,
              message: `${product.name} added to cart! 🎉`,
            };
          });

          // Use the fully typed result! 💪
          if (result.success) {
            showNotification(result.message);
            updateCartBadge(result.cartSize);
          }
        }}
        disabled={inCart || product.stock === 0}
      >
        {inCart
          ? "In Cart ✓"
          : product.stock > 0
          ? "Add to Cart 🛒"
          : "Out of Stock 😔"}
      </button>
    </div>
  );
}
```

### 📊 Real-Time Analytics That Update Themselves

```tsx
export async function MetricsPanel() {
  // This component re-renders automatically when ANY metric changes! 🔄
  const metrics = app.db.metrics.current;

  return (
    <div className="metrics-grid">
      <MetricCard
        title="Revenue Today 💰"
        value={`$${metrics.revenue.toLocaleString()}`}
        trend={metrics.revenueTrend}
        onClick={async () => {
          // Drill down into details
          const details = await server(() => {
            // Complex server-side calculations 🧮
            const orders = app.utils
              .values(app.db.orders)
              .filter(
                (order) =>
                  order.date.toDateString() === new Date().toDateString()
              );

            return {
              orderCount: orders.length,
              averageOrderValue:
                orders.reduce((sum, o) => sum + o.total, 0) / orders.length,
              topProducts: getTopProducts(orders),
            };
          });

          showDetailsModal(details); // Fully typed! 🎯
        }}
      />
    </div>
  );
}
```

### 🎯 Control Your Reality

Real-time updates are amazing until they're not. Other frameworks force you to choose: either everything updates live (overwhelming users during data analysis) or you build separate non-reactive endpoints (doubling your API surface). With zero, you control the flow:

```tsx
export async function CryptoTicker() {
  const prices = app.utils.view({
    path: "crypto.prices.*",
    predicate: () => true,
  });

  return <CryptoTickerLayout prices={prices} />;
}

export async function CryptoTickerLayout({ prices }: { prices: Price[] }) {
  return (
    <div>
      <div
        onClick={async () => {
          await server(() => {
            // Actually pause/resume real-time updates!
            if (isRealtime()) {
              disableRealtime(); // 🛑 Stop the firehose
            } else {
              enableRealtime(); // 🌊 Resume the flow
            }
          });
        }}
        style={{
          cursor: "pointer",
          padding: "20px",
          background: isRealtime() ? "#eeffee" : "#ffeeee",
        }}
      >
        <h2>
          Crypto Prices {isRealtime() ? "📈 LIVE" : "⏸️ PAUSED"} (click to{" "}
          {isRealtime() ? "pause" : "resume"})
        </h2>

        {prices.map((coin) => (
          <CryptoTickerCoin coin={coin} />
        ))}
      </div>

      {!isRealtime() && (
        <button
          onClick={async () => {
            await server(() => {
              refreshData(); // 🔄 Manual one-off update while paused!
            });
          }}
          style={{ marginTop: "10px", padding: "5px 15px" }}
        >
          Refresh Data 🔄
        </button>
      )}

      <p style={{ fontSize: "12px", marginTop: "10px" }}>
        {isRealtime()
          ? "Updating in real-time. Click to take a breather."
          : "Updates paused. Click 'Refresh Data' for manual updates."}
      </p>
    </div>
  );
}

export async function CryptoTickerCoin({ coin }: { coin: Coin }) {
  return (
    <div>
      {coin.symbol}: ${coin.price.toFixed(2)}
      {coin.change > 0 ? "📈" : "📉"} {coin.change}%
    </div>
  );
}
```

**That's it.** Click to pause a real-time data stream. Click again to resume. Want fresh data while paused? Just call `refreshData()`. No WebSocket management. No subscription tracking. No separate endpoints. 🎛️

### 🎮 Multiplayer Chess (Yes, Really!)

```tsx
export async function ChessBoard({ gameId }: { gameId: string }) {
  const game = app.db.games[gameId];
  const isMyTurn = game.currentPlayer === sessionId;

  return (
    <div className="chess-board">
      {game.board.map((row, y) => (
        <div className="row">
          {row.map((piece, x) => (
            <Square
              piece={piece}
              isSelected={
                game.selectedSquare?.x === x && game.selectedSquare?.y === y
              }
              onClick={async () => {
                if (!isMyTurn) return;

                await server(() => {
                  if (!game.selectedSquare) {
                    // Select piece 🏃
                    if (piece?.owner === sessionId) {
                      game.selectedSquare = { x, y };
                    }
                  } else {
                    // Make move (with full chess logic on server!) ♟️
                    const move = validateMove(game, game.selectedSquare, {
                      x,
                      y,
                    });
                    if (move.valid) {
                      // Update board
                      game.board[y][x] =
                        game.board[game.selectedSquare.y][
                          game.selectedSquare.x
                        ];
                      game.board[game.selectedSquare.y][game.selectedSquare.x] =
                        null;

                      // Switch turns
                      game.currentPlayer = game.players.find(
                        (p) => p !== sessionId
                      );
                      game.selectedSquare = null;

                      // Check for checkmate 👑
                      if (move.checkmate) {
                        game.winner = sessionId;
                        game.status = "finished";
                      }
                    }
                  }
                });
              }}
            />
          ))}
        </div>
      ))}
    </div>
  );
}
```

## 🚀 Events & Views: Real-Time Reactivity Without the Complexity

### Why Should You Care?

Remember the last time you had to sync UI state with a database? The manual subscriptions, the cache invalidation logic, the race conditions? 😱

**zero**'s events and views system eliminates all of that. You get real-time, reactive data collections that update automatically, with zero boilerplate. 🎉

This isn't another state management library. It's a fundamentally different approach where your data tells you when it changes, and your filtered collections maintain themselves. 🔮

### The Events System: Know Everything, Instantly ⚡

**The Problem It Solves**

Traditional databases force you into a request-response pattern. You query data, display it, then hope you remember to refresh it when something changes. Or worse, you implement polling. 🤮

Remember tRPC? The "simple" type-safe API layer? Hours configuring schemas, massive compile times, and then your junior dev forgets to turn off React Query's implicit caching and you spend 3 hours debugging why data isn't updating. 😭

**zero** flips this model: your database pushes changes to you, instantly. No setup. No caching footguns. Just reactive data. 🚀

**Real-World Power**

```typescript
// Traditional approach: Poll for changes 😴
setInterval(async () => {
  const orders = await db.query(
    "SELECT * FROM orders WHERE status = 'pending'"
  );
  updateUI(orders);
}, 5000);

// zero: Real-time updates 🚀
app.db.on("orders.*.status", (event) => {
  if (event.newValue === "pending") {
    addPendingOrder(event.path.split(".")[1]);
  }
});
```

**Wildcard Subscriptions That Actually Work** 🎯

```typescript
// Monitor ALL user activity 👀
app.db.on("users.*.lastActive", (event) => {
  updateActiveUserMetrics(event.path, event.newValue);
});

// Track any configuration change, anywhere 🔍
app.db.on("**.config", (event) => {
  console.log(`Config changed at ${event.path}`);
});

// Multi-level wildcards for complex hierarchies 🏗️
app.db.on("tenants.*.projects.*.tasks.*", (event) => {
  // Tracks every task in every project for every tenant
  notifyTaskUpdate(event);
});
```

**Batched by Default (Because Performance Matters)** 🏎️

```typescript
// This won't kill your performance
for (const id of userIds) {
  app.db.users[id].status = "active";
  app.db.users[id].updatedAt = Date.now();
}
// All changes delivered in a single batch ✨
```

### The Views System: Self-Maintaining Collections 🤖

**Live Filtered Collections**

```typescript
// Define once, use everywhere 🌍
const activeUsers = app.utils.view({
  path: "users.*",
  predicate: (user) => user.status === "active" && !user.deleted,
});

// This array is ALWAYS up-to-date 🔄
console.log(activeUsers); // [...all active users]
```

**Real-World Patterns That Just Work** 💪

```typescript
// Live Search 🔍
let searchTerm = "";

const searchResults = app.utils.view({
  path: "products.*",
  predicate: (product) =>
    searchTerm === "" ||
    product.name.toLowerCase().includes(searchTerm.toLowerCase()),
});

// Multi-Tenant Isolation 🏢
const tenantId = getCurrentTenantId();

const tenantData = app.utils.view({
  path: "data.*",
  predicate: (item) => item.tenantId === tenantId,
});

// Composable Views - Automatically scoped to tenant! 🤯
const contractsWaitingMyApproval = app.utils.view(
  {
    path: "data.contracts.*",
    predicate: (contract) => contract.actionOwnerId === userId,
  },
  [tenantData]
); // <-- tenantData automatically scopes everything!

// Real-Time Analytics Dashboard 📊
const metrics = {
  totalUsers: app.utils.view({ path: "users.*", predicate: () => true }),
  activeToday: app.utils.view({
    path: "users.*",
    predicate: (u) => Date.now() - u.lastActive < 86400000,
  }),
  premiumUsers: app.utils.view({
    path: "users.*",
    predicate: (u) => u.tier === "premium",
  }),
};
```

## 🎯 Why This Changes Everything

### The Tools We Deserve

Remember when you could focus on the problem instead of the plumbing? When a todo app was 50 lines, not 5,000? When you spent more time thinking about features than configuration? 🤔

We've been conditioned to accept complexity. "That's just how modern web dev is," we tell ourselves while debugging our 47th webpack config, our useEffect that somehow runs in production but not in dev, our component that re-renders when someone types in a completely unrelated input field. 😩

**zero says no more.** 🚫

```tsx
// This is your ENTIRE voting feature. The whole thing. 🗳️
export async function VotingApp() {
  return (
    <div>
      <h1>What's your favorite language? 🤔</h1>
      <select id="language-choice">
        <option value="">Choose...</option>
        <option value="typescript">TypeScript</option>
        <option value="rust">Rust</option>
        <option value="go">Go</option>
      </select>

      <button
        onClick={async () => {
          // Get the choice from DOM - client side! 🎭
          const choice = document.getElementById("language-choice").value;

          if (!choice) {
            alert("Please choose a language! 🙏");
            return;
          }

          const result = await server(() => {
            // We're on the server now - but 'choice' just works! 🪄
            // NO BUILD STEPS. THIS IS REAL. 🤯

            // Increment vote count
            app.db.votes[choice] = (app.db.votes[choice] || 0) + 1;

            // Get current standings
            return app.utils
              .values(app.db.votes)
              .sort(([, a], [, b]) => b - a)
              .map(([lang, votes]) => `${lang}: ${votes}`);
          });

          // Show results - fully typed! 📊
          const standings = result.join("\n");

          alert(`Vote recorded! 🎉\n\nCurrent standings:\n${standings}`);
        }}
      >
        Vote 🗳️
      </button>
    </div>
  );
}
```

Look at that. 45 lines. Full-stack voting app. Type-safe. Reactive. No build steps. No npm install. No node_modules. No GraphQL. No REST. Just TypeScript.

**This is what we've been missing.** 💔

### The Bottom Line

- **Zero build steps**: Just `deno run`. That's it. 🚀
- **Implicit full-stack type safety**: Your types flow from DB to UI automatically 🔒
- **Client state magic**: Use any client variable in server functions 🪄
- **Instant reactivity**: Limited only by the speed of light ⚡
- **Pure simplicity**: No APIs, no state management, no complexity 🎯
- **Binary-efficient updates**: UI receives surgical DOM mutations, not HTML soup 🎨
- **Control when you need it**: `disableRealtime()` to pause updates, `enableRealtime()` to resume 🎛️

Stop configuring. Start shipping. 🚢

## 🚀 Get Started

```bash
# Your competition is still running npm install 🐌
git clone https://github.com/the-zero-project/zero.ts.git
cd zero.ts
deno run --allow-env --allow-net --allow-read --allow-write --allow-ffi ./src/main-vdom.ts

# You're already in production 🎉
```

## 🤝 Join the Revolution

<div align="center">
  <a href="https://github.com/the-zero-project/zero.ts">
    <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" />
  </a>
</div>

---

<p align="center">
  <strong>Built with ❤️ by engineers who missed the good old days</strong>
</p>

<p align="center">
  <sub><span style="font-weight: bold;">zero</span> - Because making software should be fun again 🎉</sub>
</p>

---

## 🌟 This Is Just The Beginning

### 🎆 What Makes This Possible

<span style="font-weight: bold;">zero</span> isn't magic (though it feels like it). It's the result of rethinking every assumption:

- **Why have an API layer?** We removed it.
- **Why serialize/deserialize data?** We don't.
- **Why manage client state?** We keep it all on the server.
- **Why send HTML when you can send instructions?** We send precise DOM mutations.
- **Why use 50 dependencies?** We use 5.
- **Why make it complicated?** We didn't. 🎉

### 🎯 Locality of Behavior: The Philosophy That Changes Everything

We're big believers in Locality of Behavior (LoB). If you've watched any of Theo's videos on why "Separation of Concerns" is often misunderstood, you know exactly what we're talking about. We agree with him strongly.

**Traditional "Separation":**

```
/src
  /components
    TodoItem.tsx      # Just the UI
  /api
    /routes
      todos.ts        # REST endpoints
  /graphql
    /resolvers
      todoResolver.ts # GraphQL logic
  /state
    todoSlice.ts      # Redux logic
  /hooks
    useTodos.ts       # Custom hooks
  /services
    todoService.ts    # Business logic
  /types
    todo.d.ts         # Type definitions
```

To understand how a todo gets toggled, you need **7 different files** across **7 different folders**. That's not separation of concerns - that's separation of _related_ concerns. It's madness. 🤯

**zero's Locality of Behavior:**

```tsx
export async function TodoItem({ todo }: { todo: Todo }) {
  return (
    <li>
      <input
        type="checkbox"
        checked={todo.done}
        onChange={async () => {
          await server(() => {
            todo.done = !todo.done; // Everything. Right. Here. 🎯
          });
        }}
      />
      <span>{todo.text}</span>
    </li>
  );
}
```

**One component. One file. One place to look.** The UI, the interaction, the business logic, the database update - it's all RIGHT THERE. When you need to change how todos work, you change the TodoItem component. Period.

This isn't just about convenience (though it is incredibly convenient). It's about cognitive load. It's about maintainability. It's about actually being able to understand your codebase six months from now.

### 🧠 Why Locality of Behavior Matters

**1. Debugging is Instant**

- Bug in todo toggling? Look at TodoItem. That's it.
- No jumping between files
- No wondering which layer has the bug
- No "wait, which file handles this again?"

**2. Onboarding is Effortless**

- New developer joins the team
- "Here's how todos work" → show them TodoItem
- They understand the entire feature in 30 seconds
- They're productive immediately

**3. Changes are Localized**

- Need to add validation? Add it in the onChange
- Need to log the action? Add it right there
- Need to check permissions? You know where
- No coordinating changes across 7 files

**4. The Code Tells a Story**

```tsx
// You can READ this like a story:

export async function ShoppingCart({ userId }: { userId: string }) {
  // "Get the user's cart"
  const cart = app.db.carts[userId] || { items: [] };

  return (
    <div>
      {/* "For each shopping cart item" */}
      {cart.items.map((item) => (
        <ShoppingCartItem item={item} />
      ))}
    </div>
  );
}

export async function ShoppingCartItem({
  userId,
  item,
}: {
  userId: string;
  item: CartItem;
}) {
  /* "Display the item" */
  return (
    <div>
      {item.name} - ${item.price}
      {/* "When they click remove..." */}
      <button
        onClick={async () => {
          await server(() => {
            // "...remove it from their cart"
            cart.items = cart.items.filter((i) => i.id !== item.id);

            // "...and log it for analytics"
            app.db.analytics.log({
              event: "item_removed",
              userId,
              itemId: item.id,
              timestamp: new Date(),
            });
          });
        }}
      >
        Remove
      </button>
    </div>
  );
}
```

The entire feature reads like a specification. The code IS the documentation.

### 🚫 What We're NOT Saying

We're not saying "put everything in one file." We're saying "put related things together." Your authentication system might live in its own module. Your email templates might have their own folder. That's fine! The point is:

**Keep related behaviors together. Separate unrelated concerns.**

A todo's UI and its toggle logic are the SAME concern, not separate ones. The artificial separation we've been taught is exactly that - artificial.

### 🎬 The Bottom Line on LoB

When you embrace Locality of Behavior:

- Your code becomes scannable
- Your features become portable
- Your team becomes productive
- Your codebase becomes joyful

This is why <span style="font-weight: bold;">zero</span> components can do "impossible" things like access databases directly. We're not breaking the rules - we're questioning why those rules existed in the first place.

**Related things should be together. It's that simple.** 🎯

What you see today is just the start. We're building the future of web development, and it's going to be **incredible**:

### 🔮 What's Next

- **AI-powered code generation** that actually understands your data model
- **Built-in analytics** that just work
- **One-click deploy** to the edge, globally

### 💬 Join The Movement

We're not just building a framework. We're building a community of developers who believe:

- Code should be simple 🎯
- Development should be fun 🎉
- Shipping should be instant 🚀
- The best tools disappear 🪄

The web is about to become fun again. And you're invited to the party.

**Welcome to zero. Welcome home.** 🏠

---

## 💔 Why We Built This

After a decade in the trenches of modern web development, we reached our breaking point. We'd spent countless hours configuring build tools, defining GraphQL schemas, managing client state, and debugging cache invalidation bugs. We'd written the same boilerplate thousands of times. We'd explained to yet another junior developer why their data wasn't updating (spoiler: React Query cache). We'd debugged yet another useEffect infinite loop, another dependency array we forgot to update, another component re-rendering 47 times per second for no apparent reason.

One night, after debugging a particularly nasty race condition between our WebSocket connection and our state management library, we asked ourselves: "What if we just... didn't?" What if we didn't have a client state? What if we didn't need an API? What if the database just... told us when things changed? What if we didn't need to spend every waking minute trying to think of another way to optimize our connections and queries. Another day, another database migration.

That moment of clarity led to months of obsessive engineering. We built a custom data pipeline. We built a custom sync engine. We built a custom binary protocol. We made TypeScript work seamlessly from database to UI. We're targeting the highest-complexity pieces of the zero-to-profitable journey - we've successfully tackled many of them, but there are many more to go.

The result is <span style="font-weight: bold;">zero</span>. It's not just a framework - it's a statement. A declaration that web development doesn't have to be this hard. That we can build amazing things without drowning in complexity. That the best tools are the ones that disappear.

We're not trying to add another layer to your stack. We're trying to remove all the layers. We're going back to the essence of what made us fall in love with programming: the pure joy of turning ideas into reality.

We hope you'll join us on this journey back to sanity, where web development is fun and rewarding, where real products get built instead of endless infrastructure, and where a todo app is 100 lines instead of 10,000. Together, we can make the web feel magical again.

**The future is simple. The future is zero.** ✨
