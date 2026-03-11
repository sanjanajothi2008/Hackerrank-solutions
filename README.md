1.DYNAMIC ARRAY
def dynamicArray(n, queries):
    arr = [[] for _ in range(n)]
    lastAnswer = 0
    answers = []

    for q in queries:
        t, x, y = q
        idx = (x ^ lastAnswer) % n

        if t == 1:
            arr[idx].append(y)
        else:
            lastAnswer = arr[idx][y % len(arr[idx])]
            answers.append(lastAnswer)

    return answers


n, q = map(int, input().split())
queries = []

for _ in range(q):
    queries.append(list(map(int, input().split())))

result = dynamicArray(n, queries)

for i in result:
    print(i)
