/**
 * This class provides many methods for First Come First Serve (FCFS). 
 * @author  Jayesh Patil
 * @version 1.0, 27/10/2022
 * @since   JDK 17
 */

import java.util.*;

import javax.management.Query;

class FCFS_Algorithm {
    Scanner sc = new Scanner(System.in);
    int noProcesses;
    public ArrayList<ArrayList<Integer>> processes;
    HashMap<Integer, Integer> ganttMap;

    //
    HashMap<Integer, Integer> processWT;
    HashMap<Integer, Integer> processTAT;
    float AverageWaitingTime = 0;
    float AverageTurnaroundTime = 0;

    public HashMap<Integer, Integer> getWaitingTimeMap(){
        return processWT;
    }

    public HashMap<Integer, Integer> getTurnaroundTimeMap(){
        return processTAT;
    }

    public HashMap<Integer, Integer> getGanttChart(){
        return ganttMap;
    }

    public ArrayList<ArrayList<Integer>> getProcesses() {
        return processes;
    }

    FCFS_Algorithm(int noProcesses) {
        this.noProcesses = noProcesses;
        processes = new ArrayList<ArrayList<Integer>>(noProcesses);

        for (int i = 0; i < noProcesses; i++) {
            processes.add(i, new ArrayList<Integer>(2));
            System.out.println("**** For Process " + (i + 1) + " (P" + (i + 1) + ") ****");
            System.out.println("Enter Burst time: ");
            processes.get(i).add(0, sc.nextInt());
            System.out.println("Enter Arrival time: ");
            processes.get(i).add(1, sc.nextInt());
        }
    }

    void printInfo() {
        System.out.println("Processes arranged in order of arrival time with process Id's");
        for (int i = 0; i < processes.size(); i++) {
            System.out.println("P" + (i + 1) + " Burst time: " + processes.get(i).get(0) + " Arrival time: " + processes.get(i).get(1));
        }
    }

    void ganttChart(ArrayList<ArrayList<Integer>> processes) {
        ArrayList<ArrayList<Integer>> processArray = sortByRow(processes);
        // ArrayList<Integer> readyQueue = new ArrayList<>();
        ganttMap = new HashMap<Integer, Integer>();

        int WTUnit = 0;
        for(int i = 0; i < processArray.size(); i++){
            // if(processArray.get(i).get(1) == i){
            //     readyQueue.add(i + 1);
            // }
            
            ganttMap.put(i + 1, WTUnit);
            for(int j = 0; j < processArray.get(i).get(0); j++){
                WTUnit++;
            }
            // readyQueue.remove(0);
        }
        ganttMap.put(processArray.size() + 1, WTUnit);
    }

    void printGanttChart(HashMap<Integer, Integer> ganttMap){
        System.out.println();

        // For table Upper line
        for (int i = 0; i < ganttMap.size() - 1; i++) {
            System.out.print("-----------");
        }
        System.out.println();

        for (int i = 0; i < ganttMap.size() - 1; i++) {
            System.out.print("| P" + (i + 1) + "      ");
        }
        System.out.print(" |");
        
        // For table Lower line
        System.out.println();
        for (int i = 0; i < ganttMap.size() - 1; i++) {
            System.out.print("-----------");
        }

        System.out.println();
        for (int i = 0; i < ganttMap.size(); i++) {
            System.out.print(ganttMap.get(i + 1) + "         ");
        }
        System.out.println();
    }

    public void calWaittingTime(HashMap<Integer, Integer> ganttMap){
        processWT = new HashMap<Integer, Integer>();
        int sum = 0;
        System.out.println();
        System.out.println("Waiting Time of Processes");
        for(int i = 0; i < ganttMap.size() - 1; i++){
            processWT.put(i + 1, ganttMap.get(i + 1) - processes.get(i).get(1));
            sum = sum + processWT.get(i + 1);
            System.out.println("P" + (i + 1) + " = " + processWT.get(i + 1));
        }
        System.out.println("Total Waiting Time = " + sum);

        System.out.println();
        AverageWaitingTime = sum/noProcesses;
        System.out.println("Average Waiting Time = " + sum + "/" + noProcesses + " = " + AverageWaitingTime);
    }

    public void calTurnaroundTime(HashMap<Integer, Integer> processWT){
        processTAT = new HashMap<Integer, Integer>();
        int sum = 0;
        System.out.println();
        System.out.println("Turnaround Time of Processes");
        for(int i = 0; i < ganttMap.size() - 1; i++){
            processTAT.put(i + 1, processWT.get(i + 1) + processes.get(i).get(0));
            sum = sum + processTAT.get(i + 1);
            System.out.println("P" + (i + 1) + " = " + processTAT.get(i + 1));
        }
        System.out.println("Total Turnaround Time = " + sum);

        System.out.println();
        AverageTurnaroundTime = sum/noProcesses;
        System.out.println("Average Waiting Time = " + sum + "/" + noProcesses + " = " + AverageTurnaroundTime);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter total number of processes: ");
        int noProcesses = 0;
        noProcesses = sc.nextInt();
        FCFS_Algorithm fcfs_Algorithm = new FCFS_Algorithm(noProcesses);
        fcfs_Algorithm.printInfo();
        fcfs_Algorithm.ganttChart(fcfs_Algorithm.getProcesses());
        fcfs_Algorithm.printGanttChart(fcfs_Algorithm.getGanttChart());
        fcfs_Algorithm.calWaittingTime(fcfs_Algorithm.getGanttChart());
        fcfs_Algorithm.calTurnaroundTime(fcfs_Algorithm.getWaitingTimeMap());
    }

    ArrayList<ArrayList<Integer>> sortByRow(ArrayList<ArrayList<Integer>> processes) {

        for (int i = 0; i < processes.size() - 1; i++) {
            for (int j = i + 1; j < processes.size(); j++) {
                if (processes.get(i).get(1) > processes.get(j).get(1)) {
                    ArrayList<Integer> list = processes.get(i);
                    processes.set(i, processes.get(j));
                    processes.set(j, list);
                }
            }
        }
        return processes;
    }
}
