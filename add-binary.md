```java

public class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int i1 = a.length() - 1;
        int i2 = b.length() - 1;
        int carry = 0;
        while (i1 >= 0 && i2 >= 0) {
            int value = carry + a.charAt(i1) - '0' + b.charAt(i2) - '0';
            sb.append(value % 2);
            carry = value / 2;
            i1--;
            i2--;
        }
        while (i1 >= 0) {
            int value = carry + a.charAt(i1) - '0';
            sb.append(value % 2);
            carry = value / 2;
            i1--;
        }
        while (i2 >= 0) {
            int value = carry + a.charAt(i2) - '0';
            sb.append(value % 2);
            carry = value / 2;
            i2--;
        }
        if (carry == 1) {
            sb.append(1);
        }
        return sb.reverse().toString();
    }
}
