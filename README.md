# Algorithmslabwork
# algorithms lab work for Y2 

class ArrayList:
    def __init__(self):
        self.inArray = [0 for i in range(10)]
        self.count = 0
        
    def get(self, i):
        self._checkBounds(i, len(self.inArray))
        return self.inArray[i]

    def set(self, i, e):
        self._checkBounds(i, len(self.inArray))
        self.inArray[i] = e

    def length(self):
        return self.count

    def append(self, e):
        self.inArray[self.count] = e
        self.count += 1
        if len(self.inArray) == self.count:
            self._resizeUp()

    def insert(self, i, e):
        self._checkBounds(i, len(self.inArray))
        for j in range(self.count,i,-1):
            self.inArray[j] = self.inArray[j-1]
        self.inArray[i] = e
        self.count += 1
        if len(self.inArray) == self.count:
            self._resizeUp()
    
    def remove(self, i):
        self._checkBounds(i, len(self.inArray))
        val = self.inArray[i]
        for j in range(i,self.count):
            self.inArray[j] = self.inArray[j+1]
        self.count -= 1
        return val

    def _resizeUp(self):
        newArray = [0 for i in range(2*len(self.inArray))]
        for j in range(len(self.inArray)):
            newArray[j] = self.inArray[j]
        self.inArray = newArray
        
    def _checkBounds(self, i, hi):  # checks whether i is in [0,hi]
        if i < 0 or i > hi:
            raise Exception("index "+str(i)+" out of bounds!")
 
    def appendAll( self, A):
        for i in range(len(A)):
            self.append(A[i])  


    def removeVal(self, e):
        for i in range(len(self.inArray)):
            if self.inArray[i] == e:
                self.remove(i)
                return True
        return False


    def clone(self):
        temp = ArrayList()
        for i in range(self.count):
            temp.append(self.inArray[i])
        return temp

    def toArray(self):
        newA = [0 for i in range(self.count)]
        for j in range(len(newA)):
            newA[j] = self.inArray[j]
        return newA
        
    def sort(self):
        A = toArray()
        B = insertionSort(A)
        return B
        
    def interstionSort(A):
        for i in range(1, len(A)):
            insert(A[i], A, i)
        return A
    
    def insert(k, A, hi):
        for i in range(hi, 0, -1):
            if k >=A[i-1]:
                A[i]=k
                return
            A[i]= A[i-1]
        A[0]= k
        
        
        
        
A = [3,4,5]  
p1 = ArrayList()
p1.appendAll(A)
p2 = p1.clone()
print(p1.inArray)
print(p1.toArray())
print(p1.removeVal(3))
print(p1.inArray)
print(p1.toArray())
print(p2.toArray())
