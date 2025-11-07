# Download Dataset File

## Overview
**Flow ID**: `export-dataset`  
**Category**: Dataset/Corpus Management  
**Estimated Duration**: 1-5 minutes (depending on file size)  
**User Role**: All Users  
**Complexity**: Simple  

**Purpose**: This flow allows users to download their dataset as a JSONL file to their computer. This is useful for backing up datasets, sharing them with others, transferring between systems, or archiving for future use. The exported file contains all structured items with their text and vector embeddings.

---

## Trigger

**What initiates this flow:**
- [x] User manually initiates


**Specific trigger**: User wants to export dataset file, typically because:
- Need backup of dataset
- Want to share dataset with others
- Transferring to different computer or installation
- Archiving dataset for long-term storage
- Need offline copy of data

---

## Prerequisites

**Before starting, users must have:**
- [x] Application installed and running
- [x] At least one dataset uploaded or created
- [x] Sufficient disk space for downloaded file
- [x] Access to dataset details page

---

## User Intent Analysis

### Primary Intent
Download complete dataset file to local storage for backup, sharing, or transfer purposes.

### Secondary Intents
- Protect against data loss
- Enable collaboration by sharing datasets
- Migrate data between systems
- Comply with backup requirements
- Archive completed work

### Subintents
- Preserve exact dataset state
- Ensure file is usable externally
- Maintain data integrity during export

---

## Step-by-Step Flow

### Main Path

**Step 1: Navigate to Dataset Details**
- **User Action**: Navigate to Datasets page, click "View" on desired dataset
- **System Response**: Dataset details page loads
- **UI Elements Visible**: 
  - Dataset details dashboard
  - Header with dataset name
  - Status badge (Active/Inactive)
  - **"Download" button** in header (target control)
  - File size indicator badge showing dataset size
  - Dataset items list
- **Visual Cues**: 
  - Download button prominently placed in header
  - File size badge may show warning if very large

**Step 2: Check File Size**
- **User Action**: Look at file size indicator badge to understand download size
- **System Response**: Badge displays size information
- **UI Elements Visible**: 
  - Badge showing: "1,247 items • 125.5 MB"
  - If large file (>100MB): May show warning "Multipart ZIP Recommended"
  - Color coding: Green for small files, Yellow/Red for very large
- **Visual Cues**: 
  - Color indicates size category
  - Warning text if applicable

**Step 3: Initiate Download**
- **User Action**: Click "Download" button
- **System Response**: 
  - System begins generating download file
  - Loading indicator may appear
  - File generation starts
- **UI Elements Visible**: 
  - Brief loading indicator
  - "Preparing download..." message possibly
  - Download button may show loading state
- **Visual Cues**: 
  - Button disabled during preparation
  - Loading animation

**Step 4: File Generation (for large datasets)**
- **User Action**: Wait while system prepares file (seconds to 1-2 minutes for very large datasets)
- **System Response**: 
  - System loads all dataset items
  - Generates JSONL formatted file
  - Each item formatted as one line of JSON
  - File prepared for download
- **UI Elements Visible**: 
  - Progress indicator if file is large
  - Status: "Generating file..."
  - May show progress percentage
- **Visual Cues**: 
  - Animated progress for large files
  - System working indication

**Step 5: Browser Download Begins**
- **User Action**: No action required (automatic)
- **System Response**: 
  - Browser download starts automatically
  - File save dialog appears (depending on browser settings)
  - Default filename suggested
- **UI Elements Visible**: 
  - Browser download notification or save dialog
  - Suggested filename: "{DatasetName}_YYYY-MM-DD_airgapai-dataset.jsonl"
  - Folder selection (if save dialog shown)
  - Download progress indicator (browser-dependent)
- **Visual Cues**: 
  - Browser download UI appears
  - Progress bar in browser if file is large

**Step 6: Choose Save Location**
- **User Action**: If prompted, select download location and confirm save
- **System Response**: 
  - File downloads to chosen location
  - Download progress shown
- **UI Elements Visible**: 
  - File save dialog (if shown)
  - Download progress in browser toolbar/notification
- **Visual Cues**: 
  - Standard operating system save dialog
  - Browser download progress indicator

**Step 7: Download Completes**
- **User Action**: Wait for download to complete
- **System Response**: 
  - File fully downloaded
  - Browser shows completion notification
  - Download indicator shows success
- **UI Elements Visible**: 
  - Browser download complete notification
  - Downloaded file visible in downloads folder
  - File size matches expected size
- **Visual Cues**: 
  - Green checkmark or completion indicator
  - Download progress reaches 100%

**Step 8: Verify Downloaded File**
- **User Action**: Optionally, navigate to downloads folder and verify file exists
- **System Response**: File is present and has expected size
- **UI Elements Visible**: 
  - File in file manager
  - Filename: "{DatasetName}_2025-10-04_airgapai-dataset.jsonl"
  - File size matches indicator from dataset page
- **Visual Cues**: JSONL file icon in file manager

**Final Step: Dataset Downloaded Successfully**
- **Success Indicator**: 
  - File exists in downloads folder
  - File size is reasonable (not 0 KB or suspiciously small)
  - Filename is descriptive and includes date
  - Can open file in text editor to verify format
- **System State Change**: 
  - Dataset file copy created on local disk
  - Original dataset in application unchanged
  - File ready for sharing, backup, or transfer
- **Next Possible Actions**: 
  - Back up file to external storage or cloud
  - Share file with others
  - Import file into different AirgapAI installation
  - Archive file for long-term storage
  - Verify file contents by opening in text editor
  - Continue using dataset in application (original unchanged)

---

## Alternative Paths & Strategies

### Strategy A: Download Multiple Datasets
**When to use**: Backing up all datasets for archival

**Steps**:
1. Navigate to datasets list (not details page)
2. For each dataset, click name to view details
3. Click Download button
4. Wait for download
5. Return to list and repeat for next dataset
6. Collect all downloaded files in backup folder

### Strategy B: Download Before Deleting
**When to use**: Removing dataset but want to keep copy

**Steps**:
1. Open dataset details for dataset to delete
2. Click Download button first
3. Wait for download to complete
4. Verify file downloaded successfully
5. Then delete dataset from application
6. Have external copy preserved

### Strategy C: Download for Sharing
**When to use**: Sharing dataset with colleague or different installation

**Steps**:
1. Download dataset file
2. Verify file integrity
3. Document which embedding model was used
4. Share file along with embedding model information
5. Recipient uploads to their AirgapAI instance

---

## Error States & Recovery

### Error 1: Download Blocked by Browser
**Cause**: Browser security settings preventing automatic downloads  
**User Experience**: 
- Download doesn't start
- Browser notification: "Download blocked"
- No file appears in downloads

**Recovery Steps**:
1. Look for browser notification asking permission
2. Click "Allow" in browser notification bar
3. If missed, try download button again
4. Check browser settings to allow downloads from application
5. Try different browser if issues persist

### Error 2: File Generation Fails
**Cause**: System error during file creation or memory issue  
**User Experience**: 
- Loading indicator continues indefinitely
- Error message: "Failed to generate file" or "Download failed"
- No file downloads

**Recovery Steps**:
1. Try download again (click button again)
2. Refresh page and retry
3. For very large datasets, may need more system RAM
4. Check disk space available
5. If persists, dataset file may be corrupted

### Error 3: Downloaded File is Corrupted or Empty
**Cause**: Download interrupted or generation error  
**User Experience**: 
- File downloads but is 0 KB or very small
- File won't open or shows errors
- Text editor shows malformed content

**Recovery Steps**:
1. Delete corrupted file
2. Try downloading again
3. Verify dataset has items (check item count)
4. Try smaller dataset first to test download functionality
5. Check browser download completion wasn't interrupted

### Error 4: File Size Mismatch
**Cause**: Partial download or file corruption  
**User Experience**: 
- Downloaded file size doesn't match size shown in dataset indicator
- File may be incomplete

**Recovery Steps**:
1. Compare file sizes (expected vs. actual)
2. If smaller than expected, download was incomplete
3. Delete partial file
4. Ensure stable conditions (don't interrupt, enough disk space)
5. Download again completely

### Error 5: Out of Disk Space
**Cause**: Insufficient disk space for large dataset file  
**User Experience**: 
- Download starts but fails partway
- Error: "Insufficient disk space" or similar
- Partial file may exist

**Recovery Steps**:
1. Free up disk space on computer
2. Delete partial download file
3. Verify sufficient space (need at least 2x file size recommended)
4. Try download again
5. Consider downloading to external drive with more space

### Error 6: Large File Warning Ignored
**Cause**: File >100MB may take long time or cause browser issues  
**User Experience**: 
- Download is very slow
- Browser may become unresponsive
- May timeout

**Recovery Steps**:
1. Be patient (large files take time)
2. Don't interrupt browser during download
3. If timeout, may need to create smaller datasets
4. Or use multipart ZIP approach if available
5. Consider breaking dataset into topic-specific smaller sets

---

## Pain Points & Friction

**Identified Issues**:

1. **No Progress Indicator for Large Files**
   - **Impact**: Users unsure if large file download is progressing
   - **Frequency**: Datasets > 100MB
   - **Potential Improvement**: 
     - Show download progress percentage
     - Display estimated time remaining
     - MB downloaded / total MB indicator
     - Speed indicator (MB/sec)

2. **No Multipart Download Option**
   - **Impact**: Very large files may fail to download as single file
   - **Frequency**: Datasets > 500MB
   - **Potential Improvement**: 
     - Automatic splitting for very large datasets
     - Option to download in chunks
     - Resume capability for interrupted downloads

3. **No Format Options**
   - **Impact**: Only JSONL format available; users may want other formats
   - **Frequency**: Users with specific requirements
   - **Potential Improvement**: 
     - CSV export option
     - JSON (pretty-printed) option
     - Custom format selection

4. **Filename Not Customizable Before Download**
   - **Impact**: Auto-generated filename may not meet user's naming preferences
   - **Frequency**: Users with specific file organization systems
   - **Potential Improvement**: 
     - Prompt for filename before download
     - Customizable filename template in settings
     - Include more metadata in filename

5. **No Download History or Tracking**
   - **Impact**: Can't see what was previously downloaded or when
   - **Frequency**: Users managing multiple backups
   - **Potential Improvement**: 
     - Download history log
     - Timestamp of last download shown
     - Version tracking for datasets

6. **No Verification or Integrity Check**
   - **Impact**: Can't verify downloaded file matches source
   - **Frequency**: Important for data integrity
   - **Potential Improvement**: 
     - Checksum displayed for verification
     - Automatic verification before download completes
     - Validate button after download

---

## Design Considerations

**Following Contextual Design Principles**:

1. **Automation Opportunities**: 
   - Auto-download on schedule for regular backups
   - Auto-verify file integrity after download
   - Auto-suggest download before deletion
   - Auto-compress large files for faster downloads

2. **Simplification Opportunities**: 
   - One-click download with smart defaults
   - Automatic file naming that's descriptive
   - No intermediate dialogs or confirmations
   - Direct download without generation step for small files

3. **Transition Smoothness**: 
   - Smooth download initiation
   - Clear progress indication
   - Stay on page during download (no navigation disruption)
   - Natural completion without interrupting workflow

4. **User Trust**: 
   - File size transparency before download
   - Clear progress for large files
   - Success confirmation when complete
   - File integrity verification option
   - Downloaded file actually works when re-uploaded

5. **Cognitive Load**: 
   - Don't require understanding of JSONL format
   - Clear button labels
   - Obvious results (file appears in downloads)
   - Standard download process familiar to users

---

## Related Flows

- [Upload New Dataset](./corpus-upload.md) - Reverse operation; upload downloaded file
- [View Dataset Details](./view-dataset-details.md) - Page where download initiated
- [Create New Blockify Job](../05-blockify-processing/create-blockify-job.md) - Creates datasets to download
- [Activate/Deactivate Dataset](./corpus-activation.md) - Manage dataset before downloading

---

## Technical References

**Knowledge Base Sections**:
- src/components/datasets/index.js - Download functionality
- src/components/jobs/blockify-job-processing-screen/ui/corpus-info.js - Alternative download location
- src/utils/corpus-loader.js - Dataset loading for export
- src/utils/create-corpus-zip.js - Multipart ZIP generation (if applicable)

**Key Components**:
- Download button with file generation
- JSONL file formatting
- Browser download handling
- Large file handling with warnings

---

## Version History

| Date | Version | Author | Changes |
|------|---------|--------|---------|
| 2025-10-04 | 1.1 | [Iternal Technologies](https://iternal.ai/airgapai) | Initial comprehensive documentation |

---

## Notes

**Important Considerations**:
- Downloaded file is exact copy of dataset; original remains in application
- File is in JSONL (JSON Lines) format: each line is complete JSON object
- Each line contains: "text" field (content) and "vector" field (embedding array)
- Large datasets (hundreds of MB) may take minutes to generate and download
- Browser may warn about large file downloads; confirm to proceed
- Downloaded file can be re-uploaded to same or different AirgapAI installation

**JSONL Format Structure**:
```
{"text": "Block content here", "vector": [0.123, 0.456, 0.789, ...]}
{"text": "Another block content", "vector": [0.234, 0.567, 0.891, ...]}
```

**File Size Expectations**:
- Small datasets (100-500 items): 1-10 MB
- Medium datasets (500-2000 items): 10-50 MB
- Large datasets (2000-10000 items): 50-250 MB
- Very large datasets (10000+ items): 250 MB - several GB

**Best Practices**:
- Download datasets regularly as backup (weekly or after major additions)
- Verify file size matches expected before deleting original
- Store backup files in multiple locations (external drive, cloud storage)
- Include embedding model information with dataset file for future reference
- Name downloaded files clearly (dataset provides timestamped name automatically)
- Test re-upload capability before relying on backup

**Download Use Cases**:
- **Backup**: Regular downloads to prevent data loss
- **Migration**: Moving to new computer or installation
- **Sharing**: Send to colleagues for collaborative work
- **Archival**: Long-term storage of completed datasets
- **Testing**: Download, modify externally, re-upload to test changes
- **Distribution**: Share prepared datasets with team members

**Common User Questions**:
- "What format is the downloaded file?" - JSONL (newline-delimited JSON)
- "Can I edit the file after downloading?" - Yes, with text editor; maintain format structure
- "Will downloading delete my dataset?" - No, creates copy; original remains
- "How do I re-upload a downloaded file?" - Use Upload Dataset flow (corpus-upload.md)
- "Is my embedding model included?" - No, vectors are included but model file itself is separate; note which model was used
- "Why is file so large?" - Contains both text and vector embeddings (arrays of 1024+ numbers per item)
- "Can I compress the file?" - Yes, JSONL compresses well; use ZIP or GZIP
- "What if download fails partway?" - Delete partial file and try again; ensure stable conditions

**Technical Details** (for advanced users):
- Each vector is array of floats (typically 384-1024 dimensions)
- Text field contains searchable content
- File is human-readable but primarily for machine use
- Can validate format by checking first few lines in text editor
- Compatible with other systems supporting JSONL with text+vector format

