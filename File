package Hash;

public class File
{
    private final int coeff = 10;
    private final int divider = (int)(1e9 + 7);

    private int[] powsCoeff;
    private int[] hashs;

    private String file;

    public File(String file)
    {
        powsCoeff = new int[file.length() + 1];
        hashs = new int[file.length() + 1];
        this.file = file;
        hashFile();
    }

    public boolean containsSubstring(String subString)
    {
        int hashLeftSubString, hashRightSubString;
        var hashSearchSubString = getHash(subString);

        for(int i = subString.length(); i < hashs.length; i++)
        {
            hashLeftSubString = (hashs[i - subString.length()] * powsCoeff[subString.length()]) % divider;
            hashRightSubString = hashs[i];
            if(hashRightSubString < hashLeftSubString)
                hashRightSubString += divider;

            if(hashRightSubString - hashLeftSubString == hashSearchSubString)
                return true;
        }

        return false;
    }

    private int getHash(String string)
    {
        int hash = 0;
        for(var i = 0; i < string.length(); i++)
            hash = (hash * coeff + (string.charAt(i) - 96)) % divider;

        return hash;
    }

    private void hashFile()
    {
        fillPowsCoeff();
        for(var i = 1; i < hashs.length; i++)
        {
            hashs[i] = (hashs[i-1] * coeff + (file.charAt(i - 1) - 96)) % divider;
        }
    }

    private void fillPowsCoeff()
    {
        powsCoeff[0] = 1;
        for(var i = 1; i < powsCoeff.length; i++)
            powsCoeff[i] = (powsCoeff[i-1] * coeff) % divider;
    }
}
