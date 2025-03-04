pq = [[0,1], [0,2], [0,3], [3,2], [4,5]]

def gr(a, b, array):
    totaly = []
    for x in array:
        is_there = []
        for y in array:
            if set(x).intersection(y) != set():
                is_there.append(list(set(x+y)))
        inter = [] # список для сбора для каждого х-ого элемента связей воедино
        for y in is_there:
            inter += y
        totaly.append(set(inter))
    for x in range(len(totaly)):
        for y in range(len(totaly)):
            if x == y:
                continue
            else:
                if set(totaly[x]).issubset(totaly[y]):
                    totaly[x] = []
                elif set(totaly[x]).intersection(totaly[y]):
                    totaly[x] = set(list(totaly[x]) + list(totaly[y]))
    res = list(filter(None, totaly))
    for x in res:
        if a in x and b in x:
            return f"Связаны"
        else:
            return f"Не связаны"



print(gr(0, 3, pq))