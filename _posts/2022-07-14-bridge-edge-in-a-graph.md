---
layout: post
title: Bridge edge in a graph                    
summary:
tags:
    - graph
    - greedy
    - geeksforgeeks
    - cpp
    - medium
minute: 12 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/problems/bridge-edge-in-graph/0/?track=DSASP-Graph&batchId=154)  

Given a Graph of `V` vertices and `E` edges and another edge(`c - d`), the task is to find if the given edge is a Bridge. i.e., removing the edge disconnects the graph.

Note: It is assumed that negative cost cycles do not exist in the input matrix.

**Your Task:** 
You don't need to read input or print anything. Your task is to complete the function `isBridge()`  which takes number of vertices `V`, the number of edges `E`, an adjacency list `adj` and two integers `c` and `d` denoting the edge as input parameters and returns `1` if the given edge `c-d` is a Bridge. Else, it returns `0`.


**Expected Time Complexity:** `O(V+E)`           
**Expected Auxiliary Space:** `O(V)`


### Examples

**Example 1:**   


```
Input:
```

<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAVUAAAFsCAIAAADzG70cAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAAhdEVYdENyZWF0aW9uIFRpbWUAMjAyMTowMTowNyAxNDoxNzoxMpt6HAEAACT2SURBVHhe7d0LVFT3vS/wP8xbZAB5iMDACAoiSVQQAdHRkBhSFY2NGqNRqeZxTk3TxJW06elpb25zbK1pTOtp11kxOY3GiAmPxAfERxJjRlFRIIqiyHMQeSioA/KYFzN3B3+3K7e3J03CAPs/+/tZrAnf317IXmvyZe89s2dvL5fLxQBAkrzpvwAgPeg/gHSh/wDShf4DSBf6DyBd6D+AdKH/ANKF/gNIF/oPIF3oP4B0of8A0oXz/6Wit7e3srLSZDI1Nzc3tTRZrJbuO912i12ukvtofdQqdeS4yNDQUL1eHx8f7+/vTz8GHg3993Bms9loNJaWlTY2NconydvHt5siTU1hTXa13aq1OlQOmU2m7lQrLIoxrWP0rfqx9WMVlxUB2oDkacmzZs2Kioqifwg8EfrvsWpqagoLCysuVdhT7CfSTjTFNTnlTlr2zwSYAmaUzgg7HjZGPebheQ/PmTNHoVDQMvAg6L8HamxszM3NvdJ0pXZRbfHsYmEjTwu+O91l3YNFD6oaVIuzFs+bN08mk9EC8Ajov0ex2+35+fmfGT8zLTF9nvH5t9/gf7NxjeMW5C7wu+G3ft36+Ph4mgL/0H/PIWz2/7jtj2a9OXdtbq+2l6buk1qWet/O+2ZMmbFmzRocDngG9N9DFBcX79i141L2pZOpJ2k0BNQW9bq31/m1+D3//PMhISE0BW6h/56goKDgyIkjRRuLmnXNNBpKjx15LGBvwEsvvhQdHU0j4BP6z709e/YYK4zv/eK9bm03jYbeD778QeT2yI0vbIyNjaURcAjn//EtLy/veOXxd3/57nCWX3Bw2sG6DXWvb33dZDLRCDiE/nPMaDR+dvKzXS/v6h3t/lf7/qlP7/m0Y33H1q1bzWYzjYA36D+vqqur33v/vaKfFXWPHtYt/9d9mPyhLcP2xhtv9Pf30wi4gv5zqa+v789/+fOlpy9dG3eNRiPkzUfe7NJ0FRYWUgauoP9c2rFjR9+UvuKpxZRHVMFTBUUHi65dG+G/RPA9oP/8qaysrKiu2LlqJ+WR1hTYZF5qfvfddykDP9B/zjidzl27dlWvrLar7DQSgfz785tuNgl/mCgDJ9B/zhiNxp7RPUeTj1IWB5fMdXnp5dzcXMrACfSfJy6X68CBA6eXnaYsJl+kftHa1VpXV0cZeID+86S8vNzuYy+NK6UsKl6sJaPls88+owg8QP95cvjw4foF9RTE59M5n546c8pqtVIG0UP/uWE2m+tN9YcTD1MWH6vWyiawiooKyiB66D83Tp8+7ZPk41B8/4v5DIPLiZeFgxQKIHroPzfKysqqUqooiNXFaRdLz4vy5Qn4R9B/Pjgcjrq6upOThvDaHm7RE9xjZdaOjg7KIG7oPx/q6+t9w3y71SP2UZ9vzxJjEdaWAogb+s+Hr95Xn0jfu8FRxjIZG8/YNMZ+z5hbzyQ0jTc1NjZSAHFD//nQ1tZmHuemj9nvZ+whxq4ztpaxyYz9grHHaYlbtIe0N91oogDihv7zQeh/W2gbhcFwMPYsY3GMnWbsFcZ2M/Y7xgoYO0TLB68nqKelo4UCiBv6z4eOjo7GYHfsVH/BmLBt3sCYmgbsp4yNYsx9H97rC+wz38IVgfiA/vOhr6/vtuY2hcE4M/CYOvB4l/CH4F7GTlAaPLvabreK6LOJ8A3Qfz5YLJYudReFwbh7YK4bePybcMaaGXPTJbwcSke/FZcD4wP6zwebzWZVuuO8+p6BR5+Bx7/RMOYU9jEoDZJT6XTZcVF5PqD/fFAKbEoKgyEfePy7et6Nbvp/QWaVeSm9KIC4of98UKvVWouWwmD4Djz+3WlEQlQM7AW4g9wil6vv/pkBsUP/+aDRaPz6/CgMxoSBx6sDj38jxKivPsDvFoo+hUKDu4PyAf3nQ1BQkK797161+17SBh6PDzzedYuxi4ylUxo8n3afgKAACiBu6D8fQkNDw9rCKAxGEmNTGHuDsbtn6AhH/r8YOCnoyYHoDr5tvpGhkRRA3NB/Pgj992t1x/6/4C3GOgfe83+CsWTGtjP2AmOzaOHgBbYGRofivsB8QP/5EBMT413jpidL6Px5xtYxdmPgI0D5jG2lJW4RURMxIebuywwgdug/H6Kjo7tbutWWv521OzhC7V9j7AhjeYw9SjO3UFgUyhalsLaUQdzQfz7I5XJho5pcJWy7RS24Kjg0JlRYW8ogbug/N5KSkhJKEiiIVUxJTEZSBgUQPfSfG6mpqbYym7ddvE+ZsG66Ml16qvveS4Qhhv5zw9/fP0YfYyg3UBafiPKIcfpxwnpSBtFD/3mSmZk5qWgSBfGZWjR1ReYKCsAD9J8niYmJmh5N/JV4ymISfCU4uCc4KTGJMvAA/eeJl5fXoqxFs/NmUxaT5Lzkx7IeE9aQMvAA/eeMwWDw7/ZPPiuuNwIjzkbounUPGB6gDJxA/znj7e29ZvWaqTlTZVYZjUaasCZpOWnPrn5WWDcaASfwhPEnISFhWuy0pbuXUh5p03dPT4xNvCfhHsrAD/SfS9nZ2cHng+89dy/lkRN2Liz+fPxPs39KGbiC/nNJo9H8ZMNPZmyfEdgaSKORoG3Vztk+5+UNLwvrQyPgCvrPq9jY2DUr1izesljVraLR8BJ+77wt83604kdxsXE0At6g/xwzGAwPz3x45eaVym53XBr0uxB+Y+bmzPkz588zzKMRcAj959uyZcvmJcxbtWmVqmv49gKE3zV/0/wFCQvWLVtHI+CTl8uFS7Vzr6CgoPBE4b6N+27r3HGPoG/k1+T34NYHs2ZlrX10LY2AW+i/hyguLv7vXf99JvtMZWoljYZA5OnI9B3pT69+em76XBoBz9B/z9HY2Pj6ttev6a99vPZjq9YdNwv6GmGfP21nWowp5lfP/SoqKoqmwDn036PY7fb8/PzDxsMVSyrOZ5x3yp20YBC8Hd4xR2OSPkrKMGRkL81WKHBtf8+B/nsgYUcgJzenqqnqy0VfXp592aFy0ILvSG6V64/rE/cnTtBNeHr509jsex7032PV1NTsLdx74dKFmyk3y9LK2uPav+XugLDBD74SPOHUhKiSqAmTJzyx8ImJEyfSMvAs6L+HM5vNRqOxuKy4uanZNsl2dfzV1sjWrrAuu9pu1VqFXQNhIy8c2yssCm2LNuBqgK5Bp63SBumCDEmGBwwP4GI+ng39l4re3t7KykqTydTQ3HC15arFarHdsTksDrlarvBVqFSq0LDQSeGTxuvHJyQkjBo1in4MPBr6L2krV67MycmhANKD8/8ApAv9B5Au9B9AutB/AOlC/wGkC/0HkC70H0C60H8A6UL/AaQL/QeQLvQfQLrQfwDpQv8BpAv9B5Au9B9AutB/AOlC/wGkC/0HkC70H0C60H8A6UL/AaQL/QeQLvQfQLrQfwDpQv8BpAv9B5Au9B9AutB/AOlC/wGkC/0HkC70H0C6vFwuF30LHq2jo+Pg5YMVTRXtre19bX39tn55p9zb5u1UOe1au7fKWzFOERwaPFE/8ZH4RyL8I+jHwKOh/x6urqFu9/HdVV9W2fpsbQltt/S37oy7cyf0jkPlsPhb+hX9MptM3alWWBS+rb7C15j6MWMvj/XSekVMi1g9a3ViVCL9Q+CJ0H/P1N/ff9h4OP9Qvtlqrpld0zSjqVPXScu+hQBTQERpRPTxaLVa/eC8B9fOWatQKGgZeBD039MIT+iRz4/s2bunJbzlfNb5G5Nv0ILvJeRyyKSiSWENYQ9lPbRm3hqZTEYLwCOg/x6loaFh21+31SnrilcV34q+RdNB82/0n5I7JepG1MZ1G6fET6Ep8A/99xDC8/jh3g/3frL35OMn62fX09StIsoiUnampE5J/eman+JwwDOg/56gu7v7jT+/UeGoKHy20OJvoekQkFvkM9+emdCS8Mrzr4SEhNAUuIX+c+/mzZu/+d1vLiRdOPbYMZf3cDybsUdi0/am/frFX0dHR9MI+IT+8621tfXV3716fv75kw+fpNGwCP8yPGN7xr+/8O+xsbE0Ag7h/D+Omc3mTZs3lf+wfJjLL2ie1nxkw5FNWzc1NDTQCDiE/vPKYrFs/v3m+gfqS+aW0Gh4Xb/n+hdPfvHbrb+9dcttbzTAMEP/efXWW2+1TGg5uOgg5ZHQOL2xNLP0t6//1uFw0Ai4gv5z6dixY5dbLu9es5vyyDm38FxtUG1uXi5l4Ar6z5+Ojo6c93MO/uSgU+Gk0Yg69OShI8VHqqqqKAM/0H/+vPfee/aH7aYwE+WRZvW1FmcXb39nu9Mpir9H8O2h/5y5ePFiTWPN7gUjv+f/dbXTa2/43hCOSigDJ9B/znz44Ydty9vsCjtl0Ti06tAHBR/ghUC+oP88qa6uvnH7xr6UfZTF5Ob4m72RvadOnaIMPED/eVJUVNS3sK/fu5+yyBx/+HjhoUIKwAP0nxs9PT0XKy/uTd9LWXwa72u83n29qamJMoge+s+NkpKSoPuCbqlFfLKdF2uf0X7mzBmKIHroPzfOnj17Ne0qBbE6O+PsybPD/WEE+N7Qfz709/dXV1cbJxspi1VHTEd7e7twqEIZxA3950NDQ4PfWL8WnxbKYuXydjmjnbW1tZRB3NB/PgiNksUOwbU3/8RYPn3rLs0Tmuvrh+QCZOB26D8fWltbu8K6KLjLXsY2MlZOyV2axjU1X2+mAOKG/vOhra3teuh1Cm7xNmMrGBuCE/bvBN1puoG3APmA/vOho6OjIdhNV9oxMfYDxp5iLIkG7tUb1HvrJq4Iwgf0nw99fX0dmg4Kg/QpY6WM/Rdje2jgXnaN3W4V3ccT4B9C//lgsVi61G46/s8c2AX4l69O1xkKDqXDYcWngPiA/vPBZrP1KN30prqOMR/6dig4FU6XHReV5gP6zwelUim3ySmIm8wm81IOza4FuBv6zwe1Wj3aMpqCuMktcpkatwnlA/rPB41G49fnR0HcFH0KhQZ3B+QD+s+HoKCg0PZQCuLm0+6jDdJSAHFD//kQGhoa3hZOQdx823wjQiMogLih/3wQ+j+mdQwFcfNr9YsNxU0B+YD+8yEmJkZW4+4X1eSM6RkLoOQuETURsTHoPx/Qfz5ER0f3tfQpLG59XW0cYw2MvUTJLYQ11LRocF9wXqD/fJDL5RNjJk6umkxZrIKrggNjAoW1pQzihv5zIykp6b6S+yiIVVRJlCHJQAFED/3nRmpqqqxM5m0X71MmrFtUWdS81HmUQfTQf274+/tP0E9IKE+gLD4R5RGB+kBhPSmD6KH/PHk48+GkoqH51L47TC6avCJzBQXgAfrPk8TERG2PNuxKGGUxCb4SHNwTnJ6YThl4gP7zxMvLa0nWkvvz7qcsJlPypgjrJqwhZeAB+s8Zg8EwtntszNkYyuIQcTYirDtssWExZeAE+s8Zb2/vdavXpeeky6xi+YytsCbTc6ZvWL1BWDcaASfwhPEnISFheuz0ubvnUh5p03ZPi4mNmZEwgzLwA/3n0pPZT044P0F3Tkd55ISdCxPW5NXsVykDV9B/Lmk0mo0bNs7dPlfbOpKftBd++8ztM4U1EdaHRsAV9J9XsbGx61esn79lvqpbRaPhJfzeuVvmPrLikeTYZBoBb9B/js0xzFk0c9HCzQuV3UoaDRfhN96/+f6UmSmrDKtoBBxC//n2+LLHFyYsXLRpkapr+PYChN/14KYHUxJS/m3Zv9EI+CR75ZVX6Fvg09R7p/Z39rvedTUnNFv9rDQdMn5Nfhm/y5iZOvNXy39FI+CWl8uFWzV4AmOx8c1db57IPnE19SqNhkDk6cgZO2YsXr34ifQnaAQ8Q/89R2Nj46vbXq3R15SsLbFq3bwjIOzzJ+1M0pl0P3/u59OiptEUOIf+exS73f7X/L9+bvy8fEl5XUadU+6G+3t7O7xjjsbc99F9cYa4V5a+olDg2v6eA/33QMKOwH/m/qepyXR+0XnTbJND9T3vxim3yvXH9Qn7E8boxjy3/LmpUVNpAXgK9N9jVddUby/cfu3StfqU+qtpV9vj2r/l7oCwwQ++Ehx5KlJfotdO1q5fuD5tYhotA8+C/ns4s9n8kfGjE2Unepp6rk+6fnP8zc7Izq6wLrvabtVahV0DYSMvHNsrLApti9bvqt+YhjEhVSFKnfKepHvWG9YH+wfTPwSeCP2Xit7e3tLK0hJTydXmq+YWs9PqdN52ejm8XHIXC2DeKu/RYaPDw8Pv09/3UMJDo0aNoh8Dj4b+S9fKlSvvfpOTk3P3G5AanP8HIF3oP4B0of8A0oX+A0gX+g8gXeg/gHSh/wDShf4DSBf6DyBd6D+AdKH/ANKF/gNIF/oPIF3oP4B0of8A0oX+A0gX+g8gXeg/gHSh/wDShf4DSBf6DyBd6D+AdKH/ANKF/gNIF/oPIF3oP4B0of8A0oX+A0gX+g8gXeg/gHSh/wDS5eVyuehb8Gi9vb2VlZVVpqrq5urWlla71e647XA5XEzGFGMUMpUsaFxQZGhkoj5xcvxkf39/+jHwaOi/hzObzUeNR4+VHeto6jBPMl8bf60zsrMrrMuutlu1VofKIbPJ1J1qhUXh2+orfIXUh4ReDh2lHTV92vT5s+ZHRUXRPwSeCP33WDU1NXsK91Rfqr6acrU6rbo9rt0pd9KyfybAFBBRGjH5+GQ/td+j8x69f879CoWCloEHQf89UGNj4zu571Q3VZcuKm2Y3SBs5GnBdxdyOSSpKCm0IXRp1tLMeZkymYwWgEdA/z2K3W5/P//9I8YjZ5ecrcmo+fYb/G/m3+g/K3eW/ob+x+t+HB8fT1PgH/rvOYTN/pZtW+r0dcfWHhOO7WnqPlFlUbN3zjZMMWSvycbhgGdA/z1EcXHx9l3bj2cfb0htoNEQkFvkC95eMLFl4kvPvxQSEkJT4Bb67wnyC/L3nthbuLGwU9dJo6GUfCR56t6pL7/4cnR0NI2AT+g/93L25BRVFBX8omAo9vn/J/FfxqdvT3/phZdiY2NpBBzC+X98y8vLK6osyv9l/nCWX3B52uVjG45t2brFZDLRCDiE/nPMaDQWniwseLnANtpGo2FUe09t+fry17a+ZjabaQS8Qf95VV1dveP9Hft+ts86eli3/F/3ZfKXdRl1r7/xen9/P42AK+g/l/r6+v70lz8df/p457jheMHvGxx+5HCzprmwsJAycAX959I7O95pmtJUO7WW8ojKeypv/8H9165dowz8QP/5U1lZWVZd9vGqjymPtO7A7itLr+x8dydl4Af6zxmn07lj146SlSX9KhEdcp+8/2T9zXrhDxNl4AT6zxmj0Xhz9M3KZHE1zSVzlSwt2ZO7hzJwAv3nicvl2ndg37FlxyiLSWVqZXNXc11dHWXgAfrPk/Ly8m6f7oa4ITzD//vzYlcyrnzy2ScUgQfoP08OHz58YcEFCuJTPqf81JlTVuuInY8A3xX6zw2z2Vxrqj2beJay+Fi1VtsEW0VFBWUQPfSfG6dPn/ZO8nYq3HNJjyFyMfHimfIzFED00H9ulJWVXUgR787/XQ3TGsrOl1EA0UP/+eBwOGrras9NOkdZrHqCe2zM1tHRQRnEDf3nQ319/aiwUTa1+z7nd4uxU4xdYszdxxPdMd3C2lIAcUP/+VBXV+ec6KamXmNsPmOBjM1kLIGxsYy9RUvconF8o6kRFwXgA/rPh7a2ttvjblMYDDtjDzNmZOwvjNUwdpyxyYw9zdj7tHzwzCFm0w30nw/oPx+E/reEtlAYjCLGKhnbzNiPGZvA2KyBSRBjr9HywesJ6mntaKUA4ob+86Gjo+NasJs+YDuXsQX07VdGMzaRsauUBq8vsK/rVhcFEDf0nw99fX1dGneU6hHGPmdsPKWvmBm7wFgMpcGzq+0O6/e/4xAMJ/SfDxaL5Y76DgX3epmxbsb+ldLgOZSOfisuB8YH9J8PNpvNrrRTcKP/YOxNxpYxtpYGg+dUOl12XFSeD+g/H5RKpcamoeAWTsZeYOxXjGUxtotmbiGzyryV+P+KD3ie+KBWq7UWLYXB62FsCWN/ZOwpxj5kTEVjt5Bb5DI1bhPMB/SfDxqNZkzfGAqDZGYsg7FCxn7P2HahrzR2F0WfQqlRUgBxQ//5EBQUFNUeRWEw+gfeAihl7F3GfkYz9/Jp9wkMCqQA4ob+8yFU0BZKYTDeYuwLxlIYczC282tf79HywfNt89WH6imAuKH/fBDq79/qT2Ew7l6k+xRj2f/v19MDc3cIbQ2NDI2kAOKG/vMhJibGVeOON9XyGWv4R1+XafnghdeEC2tLAcQN/edDdHR0Z0unv2XQuwDhjAn75v//lzteWxAoLApZi0xYW8ogbug/H+RyubBRNVQZKItVcFWwLkYnrC1lEDf0nxtJSUkTSyZSEKuEkoQ5SXMogOih/9xITU3tLOvU2N16FqBbedu9x5aNFdaTMoge+s8Nf3//8frxWeVZlMVHV66L0kcJ60kZRA/950lmZmZYURgF8UkpSlmSuYQC8AD950liYqJ3j/f9V+6nLCbBV4IDewKFNaQMPED/eeLl5ZWVlTUtbxplMTHkGZZnLRfWkDLwAP3njMFgUHQrlpwV12525NnIiO4IYd0oAyfQf854e3uvXr06LCfMx+pDo5Ems8pm58x+avVTwrrRCDiBJ4w/CYLYhCd3P0l5pM3dPTclNkVYKcrAD/SfS9nZ2a7zrvnn5lMeObpzugnnJzyZLZY/RvCdoP9c0mg0GzZs0G3XTW6dTKORoG3VZmzP2Lhho7A+NAKuoP+8io2NXbli5dwtc0O6Q2g0vFTdqqwtWetWrBPWhEbAG/SfYwaDYe7MuY9vfnxMt5suDfatKbuVj25+dNHMRXjNn2voP9+WLVuWkpDyxKYnQrqGby9A1aVatmnZgoQFy5ctpxHwycvlwqXauVdQUHD0xFHjRuNF3UUaDRn/Jv9FWxdlzcpa+uhSGgG30H8PUVxc/O6ud1uzWw+kHqDREIg7HZe2I+3J1U+mp6fTCHiG/nuOxsbGbdu2OfSOnLU5HdoOmrqJsM+/cOfCcFP4xuc2RkW56WpBMNLQf49it9vz8/M/N37evaQ7LyPPIXfDfTi9Hd4zjs6Y9NGkhwwPLV26VKFQ0ALgH/rvgYQdgdzc3Pqm+luLbh2YfaBP1UcLviO5VT79+PRJ+yfF6+IfW/4YNvueB/33WDU1NYWFhRcvXdSkaMrSys7EnXHKnbTsGwkb/KgrUamnUpUlyimTpyxcuHDiRLFfdwy+H/Tfw5nNZqPRWFZWdrXpqu8k3+7x3S2RLVfCrrSr261aq0PlEDbywrG9xqKJa4kLvxru1+BnrbJG6aKmJ003GAy4mI9nQ/+lore3t7Ky0mQyNTc3t7S0WK3WrjtdVotVpVZpfbUqlSosLCw8PFyv1yckJIwaNYp+DDwa+i9pK1euzMnJoQDSg/P/AKQL/QeQLvQfQLrQfwDpQv8BpAv9B5Au9B9AutB/AOlC/wGkC/0HkC70H0C60H8A6UL/AaQL/QeQLvQfQLrQfwDpQv8BpAv9B5Au9B9AutB/AOlC/wGkC/0HkC70H0C60H8A6UL/AaQL/QeQLvQfQLrQfwDpwv0/peJv9/+90nyluaXZZrXZ7tj6Lf3eKm+lVilXyUPHhUaHRsfp4+Lj43Hbb4lA/z2c2Ww2Go1flH1xvel676Re03jTzcibXWFddrXdqrU6VA6ZTabuVCssCt9WX+FLV68LvBzoo/VJnZb6wKwHoqKi6B8CT4T+e6yampqCwoLKS5VtKW0X0i60x7U75U5a9s8EmAL0pfr44/EB6oBH5j0yZ84chUJBy8CDoP8eqLGx8b3c96qaqsoWldXMrhE28rTguwu5HJJWlBbUELQ0a+m8efNkMhktAI+A/nsUu92el5932Hi4fEn5pYxL336D/838G/0fyH0g4kbEM+ueiY+PpynwD/33HMJm/w/b/tCobzyy9ohwbE9T94kpi5m1c9bsKbPXrFmDwwHPgP57iOLi4rd3vX0y+2R1ajWNhoDcIv/h2z8c3zJ+4/MbQ0JCaArcQv89QUFBwf4T+/dv3G/WmWk0lGYfmR2/N/7nL/48OjqaRsAn9J97e/bsOVRx6INffDAU+/z/k6lfTk3envziCy/GxsbSCDiE8//4lpeXd6jy0Pu/fH84yy84N+3cyQ0nX9v6mslkohFwCP3nmNFo/Pjkxx+8/IFttI1Gw6jynsrK9ZV/2PoHs3k4DjpgKKD/vKqurt75/s59P9tnHT2sW/6vO5V86lrGta1vbO3v76cRcAX951JfX9+2v2w79fSp2+Nu02iE7HtkX5umrbCwkDJwBf3n0o4dO9qmtF2eepnyiMp9KvfAwQPXrl2jDPxA//lTWVlZXl2+d9VeyiOtM7Czfmn9znd3UgZ+oP+ccTqdO3ftLF1Z2q8S0SH3sfuPmW6ahD9MlIET6D9njEbj7dG3zyWfoywOLpmrdGnp+7nvUwZOoP88cblc+w/sNy4zUhaTc6nnmrua6+rqKAMP0H+elJeX9/r0VscN4Rn+358Xq82o/eyzzygCD9B/nhw+fLhygXiPsc/MOVN8pthqHbHzEeC7Qv+5YTab60x1JxNPUhYfq9baP6G/oqKCMoge+s+N06dPy5PkToV7LukxRC4mXjxbfpYCiB76z42ysrLKFLG/wVY7rbbsfBkFED30nw8Oh6O2rrZ0UillseoJ7rExW0dHB2UQN/SfD/X19aPDRlvV7ntpzcKYiTE7JTfqiekR1pYCiBv6z4e6urr+iW464e8OY+sY82dsPGO+jK1i7AYtcQvTeFNjYyMFEDf0nw9tbW3mcW76mP2jjO1i7EXGPmdsM2MHGHtYOMCghYN3O+S26QYuCsIH9J8PQv9bQlsoDMZxxj5h7OeM/Qdjcxl7nrH/zdiXjB2i5YPXE9TT2tFKAcQN/edDR0fHtWB3fMA2cKDw2ZS+kjDw6L4P7/YF9nXe6qQA4ob+86Gvr69T445STWbs14xNoMRcjO3+6tRdNosGg2dX2x1W9x1OwFBC//lgsVi61F0U3EI4Qv8ZY1MYy2Xsvxi7h8aD51A6+q24HBgf0H8+2Gw2u9Ktb9ZVMGZkzMyYbOD4v5fGg+dUOl12XFSeD+g/H5RKpdqmpuAWixg7zdhVxn7D2JuM/ZjGgyezyryV+P+KD3ie+KBWq7UWLQX32shYEmN7GHPTuUVyi1ymxm2C+YD+80Gj0QT0BVAYjPMDR/t/d7uA6IHJHUqDpOhTKDVKCiBu6D8fgoKCotqjKAxG4cCu/ieUvuJg7CxjYwfeGnQHn3afMUFjKIC4of98CA0NHdc2jsJgrBEKOrDPf/caQt2MPfV/3wvwGpgMmm+bb1SoO/5UwdBD//kg9F/b6o7jfx1jBQMn/McxFslYyMC5wEL5hb8IbjK2daw+VE8BxA3950NMTIxXjZs20JmM1TP2DmPrB87/F3YEfk9L3CK8JlxYWwogbug/H6Kjo7tautz2FkDAwCnA/4ux5wZe/HMfhUUhb5ELa0sZxA3954NcLhc2qulV6ZTFKrgqODwmXFhbyiBu6D83kpKS4kqEo3ZRiy+Jn5s0lwKIHvrPjdTU1Dtld5R28b617m33Di0LTUtNowyih/5zw9/fP1of/YPyH1AWH125LlIfKawnZRA99J8nmZmZUUXifWs9uSj50cxHKQAP0H+eJCYmynvkaVfEuIMdfCU4sCdQWEPKwAP0nydeXl5ZWVnJecmUxSQ9L/2xrMeENaQMPED/OWMwGDTdmsyzmZTFQXdWp+vWzTHMoQycQP854+3tvXr16uicaJVVRaORJrPKZuXMemb1M8K60Qg4gSeMPwkJCffG3vuj3T+iPNJm7Z41I3aGsFaUgR/oP5eys7MV5xVzz438mTbh58Jjz8c+k/0MZeAK+s8ljUbz7IZnY7fHjm8dT6ORoG3VZmzPeHHDi8L60Ai4gv7zKjY2dtWKVZlbMv26/Wg0vFTdqgVbFqxfsV5YExoBb9B/jhkMhoyZGU9sfsK325dGw0XZrVy8eXHWzCy85s819J9vy5YtS09IX7NpjbZraK4O+o+oulRLNi3JSsh6fNnjNAI+eblcuFQ79woKCj458cmRjUcadA00GjJ+TX4Lti5YPGvx8keX0wi4hf57iOLi4h27dtRm1x5LPUajIRB9OnrWjllPr346PV3sVyKAbwP99xyNjY1/2vanHn1Pztqcbm03Td1E2Oeft3NelCnqpedeiorC5T09BPrvUex2e35+/lHj0dYlrQczDjrlTlowCN4O73uP3jvloymZhsxlS5cpFApaAPxD/z2QsCOQm5tb01TTtKjp09mfOlTf8268cqt88vHJU/ZPidfFr1y+Ept9z4P+e6yamprCwsILly6wFHYy7WRNXM233B0QNvhjr4ydcWqGX4nfvZPvXbxw8cSJE2kZeBb038OZzWaj0VhWVmZqMqknqW+Nv9Uc2VwVVmVT26xaq7BrIGzkhWN7hUUR1hKmv6oPaghyVbkidZEzkmYYDAZczMezof9S0dvbW1lZaTKZmgUtzb3W3p47PTaLTalW+vj6qFSqyLDI8PBwvV6fkJAwatQo+jHwaOg/gHTh/D8A6UL/AaQL/QeQLvQfQLrQfwDpQv8BpAv9B5Aqxv4PDDdmba25tl0AAAAASUVORK5CYII=">

```
c = 1, d = 2
Output:
1
Explanation:
From the graph, we can clearly see that
blocking the edge 1-2 will result in 
disconnection of the graph. So, it is 
a Bridge and thus the Output 1.

```

### Constraints

+ `1 ≤ V,E ≤ 10^5`
+ `0 ≤ c, d ≤ V-1`

## Solutions

```cpp
class Solution
{
    public:
    bool vis[15000]={};
    void dfs(int node,vector<int> adj[]){
        vis[node] = 1;
        for(auto it : adj[node]){
            if(!vis[it])
            dfs(it,adj);
        }
    }
    //Function to find if the given edge is a bridge in graph.
    int isBridge(int V, vector<int> adj[], int c, int d) 
    {
        // Code here
       vector<int> temp[V];
       for(int i=0;i<V;i++){
           for(auto it : adj[i]){
               if((i==c && it==d) || (i==d && it==c))
               continue;
               temp[i].push_back(it);
           }
       }
       dfs(c,temp);
       return !vis[d];
    }
};
```

