# zalupa
#ne rabotaet hueta dranaya


def reset(serv_number, default, R):
    datas[serv_number - 1] = default[serv_number - 1]
    R[serv_number - 1] += 1
    return datas, R


def disable(data_number, serv_number, datas):
    datas[data_number - 1][serv_number - 1] = 0
    return datas


def getmax(datas, R):
    listik = []
    for _ in range(len(datas)):
        listik.append(len(datas[_]) * R[_])
    return listik.index(max(listik)) + 1


def getmin(datas, R):
    listik = []
    for _ in range(len(datas)):
        listik.append(len(datas[_]) * R[_])
    return listik.index(min(listik)) + 1



content = input().split()
centres = int(content[0])
datas_amount = int(content[1])
ops = int(content[2])
datas = []

R = []

for _ in range(centres):
    R.append(0)
    data = []
    for __ in range(datas_amount):
        data.append(1)
    datas.append(data)
default = datas



print(datas)
print(R)
print(default)


for _ in range(ops):
    command = input().split()
    if command[0] == 'RESET':
        datas = reset(int(command[1]), default, R)[0]
        R = reset(int(command[1]), default, R)[1]
        print(datas, R, default, sep='---')
    elif command[0] == 'DISABLE':
        print(default)
        datas = disable(int(command[1]), int(command[2]), datas)
        print(datas, default, sep='---')
    elif command[0] == 'GETMAX':
        print(getmax(datas, R))
    else:
        print(getmin(datas, R))

# 1 2 1
# 1 2
