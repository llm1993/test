import java.io.BufferedReader;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.Reader;
public class Test {
    public static void main(String[] args) throws Exception {
    	Process process = Runtime.getRuntime().exec("ping 127.0.0.1");
		StringBuffer resStr = new StringBuffer();
		InputStream in = process.getInputStream();
		Reader reader = new InputStreamReader(in, "Shift_JIS");
		BufferedReader bReader = new BufferedReader(reader);
		for (String res = ""; (res = bReader.readLine()) != null;) {
			resStr.append(res + "\n");
		}
		bReader.close();
		reader.close();
		System.out.println(resStr.toString());
    }
}
