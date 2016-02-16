# what-up
cs8
Here is some code to help. I'm sorry I am really busy trying to get some of my work done. As soon as I finish my work I'll take a deeper look into it
import os
os.chdir("/Users/Phillip/Desktop/")


## getList will produce text document nlist

def getList(c,ifile,ofile):
    for aline in ifile:
        if aline[0] == c:
            ofile.write(aline)

mf1 = open("0206.txt","r")
mf2 = open("nlist.txt","w")
getList("d",mf1,mf2)
mf1.close()
mf2.close()



## getList will produce text document rlist

def getReverseList(c,ifile,ofile):
    for aline in ifile:
        if aline[-2] == c:
            ofile.write(aline)


mf1 = open("0206.txt","r")
mf2 = open("rlist.txt","w")
getReverseList("f",mf1,mf2)
mf1.close()
mf2.close()



## Extra Credit: produce text document slist

def getReverseListG(s,ifile,ofile):
    for aline in ifile:
        if aline[len(aline)-1  -   len(s):len(aline)-1] == s:
            ofile.write(aline)

mf1 = open("0206.txt","r")
mf2 = open("slist.txt","w")
getReverseListG("st",mf1,mf2)
mf1.close()
mf2.close()
