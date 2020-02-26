    /*
     *
     * The function is expected to return an INTEGER.
     * The function accepts STRING str as parameter.
     */
    public static int shortestSubstring(String str) {

        String result = "";
        //put all letter into an array
        String[] letterArray = str.split("");
        //remove all duplicate letter
            String[] uniqueLetters = new HashSet<String>(Arrays.asList(letterArray)).toArray(new String[0]);
            //convert into list and sort the list
            List<String> uniqueLetterList = Arrays.asList(uniqueLetters);
            Collections.sort(uniqueLetterList);
            //Put sorted characters into char array
            char[] uniqueCharArray = uniqueLetterList.stream().collect(Collectors.joining()).toCharArray();

            int begin = 0;
            int counter = 0;
            int uniqueCharArrayLength = uniqueCharArray.length;
            char beginChar;
            Map<Character, Integer> characterMap = new HashMap<>();
            
            //put all non-duplicate characters into array
            for(char uniqueChar: uniqueCharArray) {
                characterMap.put(uniqueChar, 0);
            }

            //Start the string iteration to find the shortest path
            for(int i=begin; i<str.length(); i++) {
                //Grab the characters
                char character = str.charAt(i);
                //Jump to update statement if key is not contained in the hash map
                if(!characterMap.containsKey(character)){
                    continue;
                }
                
                //If key is found then increment the global counter to check if it reaches the unique character length
                int characterCount = characterMap.get(character);
                if(characterCount == 0) {
                    counter = counter + 1;
                }
                characterMap.put(character, characterMap.get(character) + 1);

                //Check the resulted string for further computation
                while(counter == uniqueCharArrayLength) {
                    int tempLength = i - begin + 1;
                    //Return the size of the substring if the length of the string exactly equals to the unique character array length
                    if(tempLength == uniqueCharArrayLength){
                        return str.substring(begin, i+1).length();
                    }

                    //If the length don't match, there will be some un-needed letters
                    if(result.equals("") || tempLength < result.length()) {
                        result = str.substring(begin, i+1);
                    }
                    //Change the character that begins the character iteration
                    beginChar = str.charAt(begin);

                    //If the hash map currently have the keys, then decrement the global count and change the begining counter 
                    if(characterMap.containsKey(beginChar)) {
                        int beginCount = characterMap.get(beginChar)-1;
                        if(beginCount == 0) {
                            counter = counter - 1;
                        }

                        characterMap.put(beginChar, beginCount);
                    }
                    //Increment the character beginning 
                    begin = begin + 1;
                }

            }
            return result.length();
        
    }
