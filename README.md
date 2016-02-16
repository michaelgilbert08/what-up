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


Here is another program
alphabet= "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ .,:;!?$%()"

def letterToIndex(ch):
    alphabet= "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ .,:;!?$%()"
    idx = alphabet.find(ch)
    return idx


def indexToLetter(idx):
    alphabet= "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ .,:;!?$%()"
    if idx > 72:
        print ('error: ', 'idx: ', ' is too large')
        letter= ''
    elif idx < 0:
        print ('error: ', idx, ' is less than 0')
        letter = ''
    else:
        letter = alphabet[idx]
    return letter


def vignereIndex(keyLetter,plainTextLetter):
    keyIndex = letterToIndex(keyLetter)
    ptIndex = letterToIndex(plainTextLetter)
    newIdx = (ptIndex + keyIndex) % 73
    return indexToLetter(newIdx)


def encrypt(key, plaintext):
    WARNING = "WARNING, key is less than 8 character"
    cipherText = ""
    keyLEN = len(key)
    if len(key) < 8:
        print(WARNING)
    for i in range(len(plaintext)):
        ch = plaintext[i]
        cipherText = cipherText + vignereIndex(key[i%keyLEN], ch)
    return(cipherText)

def decrypt(key, cipherText):
    decryptedText = ""
    keyLEN = len(key)
    la = len(alphabet)
    for i in range(len(cipherText)):
        decryptedText = decryptedText + alphabet[(letterToIndex(cipherText[i])- letterToIndex(key[i%keyLEN]))%73]
    return(decryptedText)

encrypt("DAVINCI", "The Cookies are under the Bed")

# Testing Code
print("===========BEGIN OF TESTING============")
passed_all_tests = True
caseCnt = 0
def compare(a, b):
    if (a==b):
        print("CORRECT")
    else:
        print("WRONG")
        global passed_all_tests
        passed_all_tests = False
        print("Unfornately, you failed this test. \nPlease tune your code and try again. Good luck!")
        exit(1)

def checkCase(key, plaintext, ciphertext):
    global caseCnt
    print("Case #{}: ".format(caseCnt))
    caseCnt += 1
    print("Encipher text \"{}\" by key \"{}\"".format(plaintext, key))
    print("Should be: {}".format(ciphertext))
    your_ciphertext = encrypt(key, plaintext)
    print("Your text: {}".format(your_ciphertext))
    compare(ciphertext, your_ciphertext)
    print("Decipher text \"{}\" by key \"{}\"".format(ciphertext, key))
    print("Should be: {}".format(plaintext))
    your_plaintext = decrypt(key, ciphertext)
    print("Your text: {}".format(your_plaintext))
    compare(plaintext, your_plaintext)

checkCase("yellowbanana", "This is the first plaintext, let us see what it can be.", "gvDNdOD)QrB)NwMNRlAvxsKDMLOcdRpDcEP) szaUNlDcsQ)KoIazK1")
checkCase("I Love UCSB!", "Learning code is like swimming. You need to code, code and code.", "i3VPSwc)r;Z7WP:Qkz73QH:q b$GSuQJp5!U!3ZBkHdJO5O8zPXMIsP;Z!q6?2Ze")
checkCase("Powerful Python", "A: (COMPLEX) example? Yes! IT I$; 100% yes", "eglc::5)Aiks6CUZKVzFaj836siZ6cmkp3sfuiPcMV")

if (passed_all_tests):
    print("Congratulations, you passed all the tests.")
else:
    print("Somthing is wrong, contact your TA.")
print("===========END OF TESTING============")

