def smallestSubstringContaining(big_string, small_string):
  ans, q, index, freqs, seen = big_string, [], 0, {char:small_string.count(char) for char in set(small_string)}, {char:0 for char in set(small_string)}
  for index, char in enumerate(big_string):
    if char in freqs.keys():
      q.append((char, index)), seen.update({char: seen[char] + 1})
      while seen[q[0][0]] > freqs[q[0][0]]: seen[q.pop(0)[0]] -= 1
      if len(x:= big_string[q[0][1]:index+1]) < len(ans) and False not in {x.count(c) >= freqs[c] for c in freqs.keys()}: ans = x
  return ans if False not in {big_string.count(char) >= freqs[char] for char in freqs.keys()} else ""

assert(smallestSubstringContaining("abcdef", "d") == "d")
assert(smallestSubstringContaining("abcdef", "fa") == "abcdef")
assert(smallestSubstringContaining("abcd$ef$axb$c$", "$$abf") == "f$axb$")
assert(smallestSubstringContaining("abcdefghijklmnopqrstuvwxyz", "aajjttwwxxzz") == "")
assert(smallestSubstringContaining("1456243561288281932363365412356789901!", "123!") == "2356789901!")
assert(smallestSubstringContaining("abzacdwejxjfxztghiwjtklmnopqrstuvwxyz", "aajjttwwxxzz") == "abzacdwejxjfxztghiwjt")
assert(smallestSubstringContaining("a$fuu+afff+affaffa+a$Affab+a+a+$a$bccgtt+aaaacA+++aaa$", "a+$aaAaaaa$++") == "affa+a$Affab+a+a+$a")
assert(smallestSubstringContaining("14562435612z!8828!193236!336!5$41!23!5!6789901#", "#!2z") == "z!8828!193236!336!5$41!23!5!6789901#")


