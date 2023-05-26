```python
import heapq

q = []

heapq.heappush(q, (2, 'code'))
heapq.heappush(q, (1, 'eat'))
heapq.heappush(q, (3, 'sleep'))

while q:
    next_item = heapq.heappop(q)
    print(next_item)

# 结果：
#   (1, 'eat')
#   (2, 'code')
#   (3, 'sleep')
```

```python
from queue import PriorityQueue

q = PriorityQueue()

q.put((2, 'code'))
q.put((1, 'eat'))
q.put((3, 'sleep'))

while not q.empty():
    next_item = q.get()
    print(next_item)

# 结果：
#   (1, 'eat')
#   (2, 'code')
#   (3, 'sleep')
```





```python
import heapq
import itertools

n, m, k = list(map(int, input().split()))

# 将每个数列中的元素放入数组中
lists = [list(map(int, input().split()))for _ in range(n)]

# 生成所有可能的组合，并计算每个组合的和
sums = []
for comb in itertools.product(*lists):
    #此函数返回笛卡尔组合(1, 1)(1, 2)(2, 1)(2, 2)
    s = sum(comb)
    if len(sums) < k:
        heapq.heappush(sums, -s)  # 将和取负数后放入最大堆中
    elif s < -sums[0]:
        heapq.heappop(sums)
        heapq.heappush(sums, -s)

# 将最大堆中的元素取负数后输出
res = [-x for x in heapq.nlargest(k, sums)]
print(*res)

```

