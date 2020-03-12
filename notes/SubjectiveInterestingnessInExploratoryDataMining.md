# Subjective Interestingness In Exploratory Data Mining

### Goal of the paper
This paper aims at providing a general mathematical framework to measure the Subjective Interestingness of a pattern given some observations. Then various applications of this framework to Exploratory Data mining are presented. Finally the framework is compared to existing work.

### Several definitions
The theoretical framework
- **Data** is defined as an element of a certain (measurable) Space.
- A **pattern** is defined as an element of the sigma-algebra associated with the measurable set.
- A pattern is said to be **present** in the data if the data belongs to this pattern.
- A **background distribution** is a probability defined on the sigma-algebra.
- An **interestingness measure** is a real-valued function taking as input a pattern and a background distribution.

### Formalization of the Subjective Interestingness
The data mining process is defined by different steps that update a background distribution that represents the belief state of the user.
Every time a user is shown a pattern, his belief state evolves, and thus the background distribution evolved.
Within this context, finding a subjectively interesting pattern must be a trade of trade of between two criteria:
- the Information content of the pattern: it is defined as the negative log probability of the pattern given the background distribution.
- The Descriptional complexity: it measures how much storage is needed to communicate the pattern. Its definition depends on the nature of the data and the patterns.

 Given this, the Information measure that can be called **Subjective Interestingness** is defined as the ratio of the Information Content and the Descriptional Complexity.
