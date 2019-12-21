# 从一个table中，根据某列唯一值查出另一列的所有对应值，横向展示。excel的vlookup只能查出一个值。
# 之前做硬件统计的时候用很复杂的excel公式做过。

#输入测试数据
sheet("A1:A6",['sys1','sys1','sys1','sys2','sys2'])
sheet("B1:B6",['cpu4','mem128','db2','cpu8','oracle'])

#获取数据
df=sheet("A1:B5")
print(df)

#获取A列的唯一值，作为检索项，放在D列
index=df[0].unique()
sheet("D",index)
#print(df[0].value_counts())

#根据检索项，查出对应值，放在E列及右侧
#c是行标
c=1
for i in index:
    result= df[df[0]==i][1]
    r=list(result)
    start_cell="E"+str(c)
    #ord获取ascii值，chr反向获取字符，控制列标。
    end_cell=chr(ord("E")+len(r))+str(c)
    cell_range=start_cell+":"+end_cell
    #写入
    sheet(cell_range,r)
    c=c+1
    
print("done")