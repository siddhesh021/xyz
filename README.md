# xyz

EXP:_02
      def convertPlainTextToDiagraphs (plainText):
for s in range(0,len(plainText)+1,2):
if s"<"len(plainText)-1:
if plainText[s]==plainText[s+1]:
plainText=plainText[:s+1]+'X'+plainText[s+1:]

if len(plainText)%2 != 0:
plainText = plainText[:]+'X'
return plainText
def generateKeyMatrix (key):
matrix_5x5 = [[0 for i in range (5)] for j in range(5)]
simpleKeyArr = []
for c in key:
if c not in simpleKeyArr:
if c == 'J':
simpleKeyArr.append('I')
else:
simpleKeyArr.append(c)
is_I_exist = "I" in simpleKeyArr

for i in range(65,91):
if chr(i) not in simpleKeyArr:
if i==73 and not is_I_exist:
simpleKeyArr.append("I")
is_I_exist = True
elif i==73 or i==74 and is_I_exist:
pass
else:
simpleKeyArr.append(chr(i))

index = 0
for i in range(0,5):
for j in range(0,5):
matrix_5x5[i][j] = simpleKeyArr[index]
index+=1
return matrix_5x5
def indexLocator (char,cipherKeyMatrix):
indexOfChar = []
if char=="J":
char = "I"
for i,j in enumerate(cipherKeyMatrix):
for k,l in enumerate(j):
if char == l:
indexOfChar.append(i)
indexOfChar.append(k)
return indexOfChar
def encryption (plainText,key):
cipherText = []
keyMatrix = generateKeyMatrix(key)
i = 0
while (i "<" len(plainText)):
n1 = indexLocator(plainText[i],keyMatrix)
n2 = indexLocator(plainText[i+1],keyMatrix)
if n1[1] == n2[1]:
i1 = (n1[0] + 1) % 5
j1 = n1[1]
i2 = (n2[0] + 1) % 5
j2 = n2[1]
cipherText.append(keyMatrix[i1][j1])
cipherText.append(keyMatrix[i2][j2])
cipherText.append(", ")
elif n1[0]==n2[0]:
i1= n1[0]
j1= (n1[1] + 1) % 5

i2= n2[0]
j2= (n2[1] + 1) % 5
cipherText.append(keyMatrix[i1][j1])

simpleKeyArr.append(chr(i))

index = 0
for i in range(0,5):
for j in range(0,5):
matrix_5x5[i][j] = simpleKeyArr[index]
index+=1
return matrix_5x5
def indexLocator (char,cipherKeyMatrix):
indexOfChar = []
if char=="J":
char = "I"
for i,j in enumerate(cipherKeyMatrix):
for k,l in enumerate(j):
if char == l:
indexOfChar.append(i)
indexOfChar.append(k)
return indexOfChar
def encryption (plainText,key):
cipherText = []
keyMatrix = generateKeyMatrix(key)
i = 0
while i "<" len(plainText):
n1 = indexLocator(plainText[i],keyMatrix)
n2 = indexLocator(plainText[i+1],keyMatrix)
if n1[1] == n2[1]:
i1 = (n1[0] + 1) % 5
j1 = n1[1]
i2 = (n2[0] + 1) % 5
j2 = n2[1]
cipherText.append(keyMatrix[i1][j1])
cipherText.append(keyMatrix[i2][j2])
cipherText.append(", ")
elif n1[0]==n2[0]:
i1= n1[0]
j1= (n1[1] + 1) % 5

i2= n2[0]
j2= (n2[1] + 1) % 5
cipherText.append(keyMatrix[i1][j1])

EXP:_07
#include&lt;stdio.h&gt;
#include&lt;math.h&gt;
// Returns gcd of a and b
int gcd(int a, int h)
{
int temp;
while (1)
{
temp = a%h;
if (temp == 0)
return h;
a = h;
h = temp;
}
}
// Code to demonstrate RSA algorithm
int main()
{
// Two random prime numbers
double p = 3;
double q = 7;
// First part of public key:
double n = p*q;
// Finding other part of public key.
// e stands for encrypt
double e = 2;

double phi = (p-1)*(q-1);
while (e &lt; phi)
{
// e must be co-prime to phi and
// smaller than phi.
if (gcd(e, phi)==1)
break;
else
e++;
}
// Private key (d stands for decrypt)
// choosing d such that it satisfies
// d*e = 1 + k * totient
int k = 2; // A constant value
double d = (1 + (k*phi))/e;
// Message to be encrypted
double msg = 20;
printf(&quot;Message data = %lf&quot;, msg);
// Encryption c = (msg ^ e) % n
double c = pow(msg, e);
c = fmod(c, n);
printf(&quot;\nEncrypted data = %lf&quot;, c);
// Decryption m = (c ^ d) % n
double m = pow(c, d);
m = fmod(m, n);
printf(&quot;\nOriginal Message Sent = %lf&quot;, m);
return 0;
}

EXP:-03_
def generateKey(string, key):
key = list(key)
if len(string) == len(key):
return(key)
else:
for i in range(len(string) -
len(key)):
key.append(key[i % len(key)])
return("" . join(key))
def cipherText(string, key):
cipher_text = []
for i in range(len(string)):
x = (ord(string[i]) +
ord(key[i])) % 26
x += ord('A')
cipher_text.append(chr(x))
return("" . join(cipher_text))
def originalText(cipher_text, key):
orig_text = []
for i in range(len(cipher_text)):
x = (ord(cipher_text[i]) -
ord(key[i]) + 26) % 26
x += ord('A')
orig_text.append(chr(x))
return("" . join(orig_text))
# Driver code
if __name__ == "__main__":
string = "GEEKSFORGEEKS"
keyword = "AYUSH"
key = generateKey(string, keyword)
cipher_text = cipherText(string,key)
print("Ciphertext :", cipher_text)
print("Original/Decrypted Text :",
originalText(cipher_text, key))
