# Quick-Sort
# 설명
하나의 리스트를 피벗(pivot)을 기준으로 두 개의 비균등한 크기로 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 하는 방법이다.
# 예제
![quick-sort](https://user-images.githubusercontent.com/126844596/223420110-da883cf7-2ff3-4fdd-be0b-2dac70fbf573.png)
# 자바
import java.util.Scanner;

public class Quick_Sort {
	
	public static int partition(int[] array, int left, int right) { // 구분점을 만드는 메소드
	    int mid = (left + right) / 2; // 원소의 중앙값을 첫 번째 원소와 교환하기 위함
	    swap(array, left, mid); // 중앙 값을 첫 번째 요소로 이동
	 
	    int pivot = array[left]; // 첫 번째 인덱스가 pivot이 된다.
	    
        int i = left, j = right;
	 
	    while (i < j) { // left < right 즉, 교차하기 전 까지 반복한다.
	        while (pivot < array[j]) { // j는 오른쪽에서 왼쪽으로 피봇보다 작거나 같은 값을 찾는다.
	            j--;
	        }
	 
	        while (i < j && pivot >= array[i]) { // i는 왼쪽에서 오른쪽으로 피봇보다 큰 값을 찾는다.
	            i++;
	        }
	        swap(array, i, j); // 찾은 i와 j를 교환
	    }
	    // 반복문을 벗어난 경우는 i와 j가 만난경우
	    // 피봇과 교환
	    array[left] = array[i]; // 어차피 i와 j가 만나기 때문에 i 또는 j를 사용하면 된다.
	    array[i] = pivot; // array[left]값을 담아 둔 pivot을 구분점의 요소에 저장
	    return i; // 구분점이 되는 인덱스를 반환한다.
	}
	 
	public static void swap(int[] array, int a, int b) { // 단순 swap 메소드
	    int temp = array[b];
	    array[b] = array[a];
	    array[a] = temp;
	}
	 
	public static void quicksort(int[] array, int left, int right) { // 실질적인 quickSort 재귀호출을 이룬다.
	    if (left >= right) { // 이 경우는 비교할 요소가 한 개일 경우이므로 메소드를 종료한다.
	        return;
	    }
	 
	    int pi = partition(array, left, right); // 위의 메소드를 통해서 구한 구분점을 저장
	    quicksort(array, left, pi - 1); // left부터 구분점 전까지 다시 한 번 재귀호출
	    quicksort(array, pi + 1, right); // 구분점 다음부터 right까지 다시 한 번 재귀호출
	}


	
	public static void main(String[] args) {
		 Scanner sc = new Scanner(System.in);
		 
		 int n =sc.nextInt();
		 int arr[] = new int[n];
		 
		 for(int i=0;i<n;i++) {
			 arr[i] = sc.nextInt();
			 
		 }
		 
		 quicksort(arr,0,n-1);
	       
		 for(int i=0;i<n;i++) {
			 System.out.println(arr[i]);
			 
		 }
	     
		
			
	       
	      
	}

}
