# Supply Chain

## Week 2
### EOQ
Deterministic EOQ (Economic Order Quantity) models are continuous-review models.
The model assumes constant demand with no lead time. Because demand is
deterministic (and there is also no lead time) and thus there can't
be stock outs. We get ZIO (Zero Inventory Order), that is, when inventory level
reaches 0, only then do we make an order. The order size is always the same,
again this is because we have constant demand.

#### Costs
The yearly cost for a certain order quantity ($Q$) is given by:
$\frac{K\lambda}{Q} + \frac{hQ}{2}$
Deconstructing this formula the first part represents the fixed costs
times the number of times we have to reorder per year. The second part
represents the holding cost. This is the triangle of the inventory level curve.

#### Non-Zero Lead Time
When we have a lead time, that is it takes some time for the order to arrive,
we have to change the model a bit. The change is not significant, because we
have the constant demand, which leads to the same order size, but at a time
period that is earlier than when IL reaches 0.

The re-order point is $r = \lambda \cdot L$, where $L$ is the lead time.
That is when IL reaches r, we make a new order.

#### Power of Two Policy
We cannot order whenever we want, instead we have some base period that
we have to account for. This could (in the example of power-of-two) be 2
and we can only order every $2^n$ where $n\in\mathbb{Z}$.

### EOQ with Discounts
In reality it often occurs that you receive discounts if you place larger
orders. These types of discount often comes in one of two types of forms:
* All-units discount
* Incremental discount

Both forms uses break points to determine when a new price is given.

#### All-Units Discount
The all-units discount has one price up until a certain point, after that the
price changes for *all* products (that have already been) ordered.

Determine the order quantity by testing for all the types of prices,
and which ones has the lowest cost. The minimum cost is either one of the
$Q^*$ or at one of the breakpoints. You need to make sure that the $Q^*$
you test is realizable.

#### Incremental Discount
The incremental discount changes the price for all orders after reaching
the breaking point. That means you do _not_ receive a discount on the
order's that are below the break point.

To determine the order quantity here we simply needs to take the one
where the cost is the lowest among all the types of prices that could
be.

### EPQ - Economic Production Quantity
Instead of ordering items, we will now produce them. The production 
rate has to be greater than the consumption rate, otherwise there
will be backorders.

### Periodic-Review (Wagner-Within)
Instead of being able to look at the IL all the time, and order once the
IL falls under a certain level (base-stock model), the periodic review
has recurring periods for when we make new orders. For example, each week
we look at the IL and then order new items if we deem it necessary (what
W-W model does).

We do *not* assume constant demand, but rather _deterministic_ demand, which
may change. We may assume that, wlog, IL is 0 at time 0, since we can simply
change the demand in the following period(s), to use the IL at hand.

Wagner-Within uses dynamic programming to iteratively choose the best strategy
for each time period.

## Week 3
We are now no longer using deterministic demand, but rather _stochastic_ demand
rates. This means we cannot guarantee that a certain solution is optimal for
all possible outcomes. We can however use the _average_ demand rate, or take
the _expected_ costs. Again, there are two types of models:
* Periodic-review
* Continuous-review

The periodic review model are base-stock models, where we order if the IL
has fallen under a certain level, when we are checking the IL. The size of the
order depends on what our base-stock level is, and we then order until we reach
that point.
The continuous review model, is similar, and sets a reorder point. That means 
as soon as the IL goes under the reorder point we make a new order of size $Q$.

#### Safety Stock
Safety stock is the amount of stock we keep so that in case of higher demand
than expected (we have stochastic demand) we can (hopefully) still fulfill
the demand.

#### Cycle Stock
Cycle stock is the amount of stock we have to keep in order to fulfill the
expected demand.

#### Demand Process
The demand may differ in how it is modeled. We may have continuous demand or
discrete demand. The difference is the type of distribution.
Even if we are using a continuous demand that can take on negative values, we
can still reasonable assume that the demand is non-negative. Especially if
we are looking at the normal distribution and $\mu > 4\sigma$ for example.

### Periodic-Review
We have a T-period horizon that we plan for. We have a base-stock level $s$,
and then place orders so that we reach level $S$, when we have $s$ or less
in stock. The order size is $S - IL$.

#### Newsvendor Model - Single Period
The product is perishable, that is if we have too much in stock, we will
have to throw it away (or salvage for a lower price). If we have to little
in stock, we will lose the sales. We can only order _before_ the demand is
observed.

> [!NOTE]
> There are multiple ways to denoted the costs
> * $h$ - holding cost, may also be denoted as $c_o$ meaning overage cost
> * $p$ - penalty/stockout cost, may also be denoted as $c_u$ meaning underage cost

*type-1 service level* - $P(D \leq S)$, that is the probability that the demand
is less than or equal to our base-stock level. This means that the service level
of type-1 is the critical ratio ($\frac{p}{p+h}$). And for non-optimal solutions
it is the CDF until that point.

#### Finite Horizon - $T < \infty$
If we have a finite horizon, we can use a similar approach as we did for
the deterministic demand, where we used the W-W model (DP-programming).

We basically make inventory decisions for each period assuming that
the optimal decisions has been made for the previous periods. We use
an order up to level, instead of an order level as we did in the 
deterministic demand model.

While evaluating the model, we need to consider different scenarios
for where our stock level could be at each of the periods. If we have a
continuous demand, this can become problematic, or if we have a large range
for a discrete demand distribution. We can solve this by truncating the range
of possible stock levels. However, this may lead to suboptimal solutions, which
we may accept, since we are looking at a stochastic model, so we already have
some uncertainty.

The solution basically reduces to a base-stock policy.

For fixed costs (associated with making an order), the policy changes a bit.
We get a non-continuous base-stock policy. That is, it is often more profitable
to make bigger orders, once we have a low enough stock level (which is below)
the base-stock level.

##### Lead Time
If we have some lead time, we may simply change the demand to be the lead time
demand. That is we multiply the demand by the lead time.

### Continuous-Review
We have a continuous-review model, where we have a reorder point $r$ and a
reorder quantity $Q$. We order $Q$ whenever the IL reaches $r$. We make use
of two simplifying assumptions. The first is that we *do* incur a holding
cost even if we have a stockout. The second one is that we only get charged
a stockout cost for the first period a unit is missing.




