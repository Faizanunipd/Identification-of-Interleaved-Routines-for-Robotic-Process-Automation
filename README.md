# Identification-of-Interleaved-Routines-for-RPA

### Interleaving Routine Generation Steps

1. **Random Selection of Routines**
   - Select 3 routine types randomly from the dataset.

2. **Timestamp Adjustment**
   - Shift timestamps of each routine.
   - Preserve original inter-event gaps within each routine.

3. **Reference Routine Selection**
   - Pick one routine as the reference.
   - Extract its inter-trace gap distribution.
   - Example:
     - Reference gaps → [1.3s, 0.8s, 1.1s, 1.6s]

4. **Update Other Routines**
   - For each trace in non-reference routines:
     - Sample a gap from the reference distribution.
     - Update trace time:
       - `new_time = previous_time + sampled_gap`

5. **Compression to Common End Time**
   - Find the minimum end-timestamp among the 3 routines.
   - Trim/compress all routines to end at this timestamp.

6. **Community Detection (Infomap)**
   - Convert interleaved routines into a graph.
   - Apply Infomap to detect structural communities.


