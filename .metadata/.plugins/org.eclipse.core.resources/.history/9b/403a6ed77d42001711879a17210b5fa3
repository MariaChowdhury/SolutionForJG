import java.util.ArrayList;

/**
 * This class takes an array of integers and counts the number of valleys or
 * peaks. Assumption, first element and last element of the array are compared
 * with following and preceding respective elements of the array
 * 
 * @author mariachowdhury
 * @version 1
 */

public class CastleCount {
	/**
	 * This method inserts the elements of the array to a list where contagious
	 * duplicates are removed
	 * 
	 * @param a
	 *            is an array of int
	 * @return list
	 */
	static ArrayList<Integer> getArrayListNoDups(int[] a) {
		ArrayList<Integer> al = new ArrayList<Integer>();
		al.add(a[0]);
		for (int i = 1; i < a.length; i++) {
			if (a[i - 1] == a[i])
				continue;
			else {
				al.add(a[i]);
			}

		}
		return al;
	}

	/**
	 * This method counts the number of castles in the valleys. Assumption:
	 * first element and last element of the array are compared with following
	 * and preceding respective elements of the array
	 * 
	 * @param a
	 *            is an array of int
	 * @return number of castles in valleys
	 */
	static int getNumberOfValleys(int[] a) {

		// duplicate contagious elements of the array are removed
		ArrayList<Integer> al = getArrayListNoDups(a);
		int count = 0;
		int i = 0;

		// decision to build a castle at the start of the array
		if (al.get(0) < al.get(1)) {
			count++;
			i++;
		}
		for (i = i + 1; i < al.size() - 1; i++) {
			if (al.get(i) < al.get(i + 1) && al.get(i) < al.get(i - 1)) {
				count++;
			}
		}

		// decision to build a castle at the end of the array
		if (al.get(al.size() - 1) < al.get(al.size() - 2)) {
			count++;
		}
		return count;
	}

	/**
	 * 
	 * This method counts the number of castles in the peaks. Assumption: first
	 * element and last element of the array are compared with following and
	 * preceding respective elements of the array
	 * 
	 * @param a
	 *            is an array of int
	 * @return number of castles in peaks
	 */
	static int getNumberOfPeaks(int[] a) {

		// duplicate contagious elements of the array are removed
		ArrayList<Integer> al = getArrayListNoDups(a);
		int count = 0;
		int i = 0;

		// decision to build a castle at the start of the array
		if (al.get(0) > al.get(1)) {
			count++;
			i++;
		}

		for (i = i + 1; i < al.size() - 1; i++) {
			if (al.get(i) > al.get(i + 1) && al.get(i) > al.get(i - 1)) {
				count++;
			}
		}

		// decision to build a castle at the end of the array
		if (al.get(al.size() - 1) > al.get(al.size() - 2)) {
			count++;
		}
		return count;
	}

	public static void main(String[] args) {
		int[] a = { 1, 0, 8, 7, 5, 5, 5, 1, 10, 9, 2, 2, 20 };
		System.out.println("content of the array:");
		for (int i = 0; i < a.length; i++) {
			System.out.print(a[i] + " ");
		}
		System.out.println();
		System.out.println("Number of castles ");
		// if the array is empty or with one element only
		if (a.length == 0 || a.length == 1) {
			System.out.println("in peaks or valleys: " + a.length);
		} else {
			System.out.println("only in valleys: " + getNumberOfValleys(a));
			System.out.println("only in peaks  : " + getNumberOfPeaks(a));

		}

	}
}
