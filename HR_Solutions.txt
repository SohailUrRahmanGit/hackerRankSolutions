var finalRank  : [Int] = []
var uniqueArray = [Int]()

func getRank(scores: [Int]) -> [Int] {
for element in scores {
    if !uniqueArray.contains(element) {
        uniqueArray.append(element)
    }
}
 return uniqueArray
}

func climbingLeaderboard(ranked: [Int], player: [Int]) -> [Int] {
 var rankedArray = ranked

 for (_,value) in player.enumerated() {
     rankedArray.append(value)
     rankedArray.sort(by: >)
     let rankTable  =  getRank(scores: rankedArray)
     if let index = rankTable.firstIndex(of: value) {
     let addedIndex = index + 1
      finalRank.append(addedIndex)
     } 
     uniqueArray.removeAll()
 }
  return finalRank
}


var ranks = climbingLeaderboard(ranked: [100,100,50,40,40,20,10], player: [5,25,50,120])
print(ranks)




func designerPdfViewer(h: [Int], word: String) -> Int {
   let largestAlphabet = 1 
   let wordCount = word.count
   let numbers = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26]
   
   let doubledNumbers = numbers.map { h[$0] }

   print(doubledNumbers)
   return wordCount * largestAlphabet
}
print(designerPdfViewer(h: [1,3,1,3,1,4,1,3,2,5,5,5,5,1,1,5,5,1,5,2,5,5,5,5,5,5], word: "torn"))


func libraryFine(d1: Int, m1: Int, y1: Int, d2: Int, m2: Int, y2: Int) -> Int {

     let dateFormatter = DateFormatter()
     dateFormatter.dateFormat = "dd-MM-yyyy"
    var fine = 0

if let bookRentDate = Calendar.current.date(from: DateComponents(year: y1, month: m1, day: d1)) {
if let bookReturnDate = Calendar.current.date(from: DateComponents(year: y2, month: m2, day: d2)) {
        print("Date:", bookRentDate)
         print("Date:",bookReturnDate)
         
         let calendar = Calendar.current
       let components = calendar.dateComponents([.day], from: bookReturnDate, to: bookRentDate)

// Access the difference in days
if let daysDifference = components.day {

print(daysDifference)
        
          var yealate = y1 - y2
        
    if yealate > 0 {
        fine = 10000
    } else if daysDifference > 1 && daysDifference < 365 && daysDifference <= 30 {
        fine = 15 * daysDifference
    } else if  daysDifference < 365 && daysDifference > 30 {
        let noOfMonths = daysDifference / 30 
        let remainingDays = noOfMonths % 30 
        fine = 500 * (m1 - m2)
    }  else { 
        fine = 0
    }
}       
}
} 
    return fine
}




func cutTheSticks(arr: [Int]) -> [Int] {
    var resultArray = [Int]()
    var newArray = arr.sorted(by: <)
    var i = newArray.count
    while i >= 1 {
           guard let minValue = newArray.min() else { return [] }
          // print("The minimum value in the array is: \(minValue)") 
           resultArray.append(newArray.count)
           newArray = newArray.filter { $0 != minValue }
           if newArray.count == 0 { break }
    }

    return resultArray
}
