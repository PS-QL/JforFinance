source: https://github.com/shc443/Converting-Python-to-J
# Converting-Python-to-J
J is so simple and consistent, albeit hard to learn.

From "Partial correlation analysis: applications for financial markets" by Professor Kenett (2014)   
The Partial Correlation eqaution can be wrttien in Python as:
```Python
cor = cor.values # n x m matrix: row = Date, col = Stocks 
pcor = np.zeros((cor.shape[0],cor.shape[0],cor.shape[0]))
for x in range(len(cor)):
    for y in range(len(cor)):
        for z in range(len(cor)):
            pcor[z,y,x] = (cor[x,y]-cor[x,z]*cor[y,z])/np.sqrt((1-cor[x,z]**2)*(1-cor[y,z]**2))
```

This can be written in J as:
```J
pcor =: 3 : '((-"2 (*"0 1 ~ )) ~ y) %"2 (%: (*"0 1 ~ ) (1-*: y))' 
``` 

