while True:
    err = "\nERROR DETECTED!\nCheck your input and try again."
    chset = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z','A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z','1','2','3','4','5','6','7','8','9','0','`','!','@','#','$','%','^','&','*','(',')','-','=','~','+','[',']','{','}',';',"'",',','.','/',':','"','<','>','?','|']
#    print("ChSet Length = {}".format(len(chset)))
    version = input("Version 1/[2]/EXIT: ")
    if version.lower() == 'exit':
        break
    elif version == '1':
        def encrypt(w):
            try:
                l = ([' ']+chset)*2
                l2 = (['_']+chset)*2
                print("Encrypted: ",end='')
                for i in range(len(w)):
                    a = l.index(w[i])+l.index(w[-i-1])
                    b = l.index(w[i])-l.index(w[-i-1])
                    print(l2[a],end='')
                    print(l2[b],end='')
            except:
                print(err,end='')
        def decrypt(w):
            try:
                l2 = ([' ']+chset)*2
                l = (['_']+chset)*2
                a = w[::2]
                b = w[1::2]
                print("Decrypted: ",end='')
                for i in range(len(a)):
                    if (l.index(a[i])+l.index(b[i]))%2 == 1:
                        d = (l.index(a[i])+l.index(b[i])-(len(l)//2))//2
                    else:
                        d = (l.index(a[i])+l.index(b[i]))//2
                    print(l2[d],end='')
            except:
                print(err,end='')
    else:
        def encrypt(w):
            try:
                l = ([' ']+chset)*2
                l2 = (['_']+chset)*2
                if len(w)%2 == 1:
                    w += " "
                print("Encrypted: ",end='')
                for i in range(len(w)//2):
                    a = l.index(w[i])+l.index(w[-i-1])
                    b = l.index(w[i])-l.index(w[-i-1])
                    print(l2[a],end='')
                    print(l2[b],end='')
            except:
                print(err,end='')
        def decrypt(w):
            try:
                l2 = ([' ']+chset)*2
                l = (['_']+chset)*2
                a = w[::2]
                b = w[1::2]
                s = ""
                print("Decrypted: ",end='')
                for i in range(len(w)//2):
                    if (l.index(a[i])+l.index(b[i]))%2 == 1:
                        d = (l.index(a[i])+l.index(b[i])-(len(l)//2))//2
                    else:
                        d = (l.index(a[i])+l.index(b[i]))//2
                    print(l2[d],end='')
                for i in range(len(w)//2):
                    if (l.index(a[i])+l.index(b[i]))%2 == 1:
                        d = (l.index(a[i])-l.index(b[i])-(len(l)//2))//2
                    else:
                        d = (l.index(a[i])-l.index(b[i]))//2
                    s += l2[d]
                print(s[::-1],end='')
            except:
                print(err,end='')
    while True:
        EDE = input("[E]/D/EXIT: ")
        if EDE.lower() == 'e' or EDE.lower() == 'encrypt':
            encrypt(input("Encrypt: "))
        elif EDE.lower() == 'd' or EDE.lower() == 'decrypt':
            decrypt(input("Decrypt: "))
        elif EDE.lower() == 'exit':
            break
        else:
            encrypt(EDE)
        print()
